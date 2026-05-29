# Tier 2 — Build / cross-dev / deploy pages

## Yes, clone macsurf and harvest from `docs/`

Run `git clone https://github.com/mplsllc/macsurf.git` and use these files verbatim or near-verbatim as the page content:

| Website page | Source file in macsurf repo |
|--------------|-----------------------------|
| Mac-side build guide / CodeWarrior setup | [`docs/codewarrior-setup.md`](https://github.com/mplsllc/macsurf/blob/master/docs/codewarrior-setup.md) |
| Linux cross-dev workflow | [`docs/cross-dev-from-linux.md`](https://github.com/mplsllc/macsurf/blob/master/docs/cross-dev-from-linux.md) |
| Deploy guide (proxy) | [`docs/deploying-proxy.md`](https://github.com/mplsllc/macsurf/blob/master/docs/deploying-proxy.md) |

All three docs are written first-person from the actual workflow and are current as of the v0.5 / fixes157a milestone (2026-05-20). You should not need to invent anything — if a question isn't answered in those files, flag it back and Patrick will write the missing section.

## Specific answers to your build-guide questions

These are confirmations of what's in the docs so you can sanity-check while harvesting:

- **CodeWarrior version:** CodeWarrior 8 Pro with the 8.3 update. Nothing older works (C89 quirks). Nothing newer was ever released for Classic Mac OS.
- **Project file:** `MacSurf.mcp` (in the CodeWarrior tree on the Mac, not the public repo — it's a binary CodeWarrior file).
- **Output format:** PEF / CFM, PowerPC-only. Targets `MWProject_PPC` with a 16 MB application partition.
- **Prerequisites:** StuffIt Expander (for the initial bootstrap zip), Mac OS 9.1 minimum, a real Power Mac G3 or G4 (or SheepShaver, with caveats). No simulator works for hardware-acceptance testing — the dev rig is a beige G3 iMac.

## Specific answers to your cross-dev questions

- **Retro68:** install at `~/Retro68/`; the PPC GCC binary lives at `~/Retro68/toolchain/bin/powerpc-apple-macos-gcc`. Build flags + include paths are in `scripts/test-build.sh` in the repo.
- **Syntax-check command:** `./scripts/verify_macsurf.sh path/to/file.c` (also in the repo).
- **File transfer to the Mac:** SCP over a reverse SSH tunnel on port 2222, key at `~/.ssh/macsurf_push`. Workflow is `tar -cf fixesNN.tar browser/...` → `scp -P 2222 -i macsurf_push fixesNN.tar patrick@localhost:~/Documents/macfiles/`. The actual laptop-to-Mac leg is handled physically (the Mac is on the same desk, connected via direct ethernet).
- **What's stubbed vs. real:** Retro68 is *syntax-check only* — it doesn't produce a real Mac binary. Real builds happen on the Mac in CodeWarrior. Retro68 catches ~90% of compile errors before they ship, which is enough.

## Specific answers to your proxy deploy questions

- **Flags:** the proxy takes nothing on the command line right now — it listens on a fixed port. Default port is documented in `docs/deploying-proxy.md`. If you need the exact number, read the file.
- **TLS cert behavior:** the proxy fetches *outbound* over HTTPS using Go's `crypto/tls` with the system root CA pool; it does not need a server-side certificate because the Mac→proxy leg is plain HTTP.
- **No systemd unit yet.** Run under `nohup` or a screen/tmux session for now — the deploy doc shows the canonical command.
- **Browser-side config:** the Mac points its HTTP proxy at the public IP / hostname of the box running the proxy. There's no MacSurf-specific config — it uses the standard Mac OS 9 system-wide proxy preference. Steps are in the deploy doc.

## What to skip

- **macSSL deploy.** Not a public surface yet. Do not write a deploy page for it.
- **Build instructions for non-CodeWarrior toolchains.** No alternative path exists. CW8 is the only supported build.
