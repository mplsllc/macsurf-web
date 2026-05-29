# Tier 1 — Easy confirmations

## GitHub links

**Both header and footer point to the same place:** [https://github.com/mplsllc/macsurf](https://github.com/mplsllc/macsurf)

Do NOT split header → macSSL — macSSL is a private sibling repo that isn't ready for public exposure yet. One link, one repo, both header and footer.

## License page

`license.html` should be a copy of the macsurf repo's [LICENSE](https://github.com/mplsllc/macsurf/blob/master/LICENSE) file (which is NetSurf's COPYING verbatim — GPLv2 with OpenSSL linking exception, plus MIT for visual artwork).

Header preamble for the page:

> MacSurf is a derivative work of [NetSurf](https://www.netsurf-browser.org/) and inherits its licensing terms: **GPL version 2** with the OpenSSL linking exception, plus the MIT licence for visual artwork. The complete licence text follows.

### Then verbatim — include the OpenSSL exception clause as-is

```
The source code, documentation, translatable messages files and UI 
definitions contained within NetSurf are licensed under the following terms:

  NetSurf is free software; you can redistribute it and/or modify
  it under the terms of the GNU General Public License as published by
  the Free Software Foundation; version 2 of the License.
  
  In addition, as a special exception, permission is granted to link the
  code of this release of NetSurf with the OpenSSL project's "OpenSSL"
  library (or with modified versions of it that use the same licence as 
  the "OpenSSL" library), and distribute the linked executables. You must
  obey the GNU General Public License version 2 in all respects for all of 
  the code used other than "OpenSSL". If you modify the code, you may 
  extend this exception to your version of the code, but you are not
  obligated to do so. If you do not wish to do so, delete this exception
  statement from your version.

All visual artwork contained within NetSurf is licensed under the terms of 
the MIT License.
```

Then the full GPLv2 text and the MIT text — both are in the macsurf repo's [LICENSE](https://github.com/mplsllc/macsurf/blob/master/LICENSE) file (Annex A: MIT, Annex B: GPL).

The Go proxy and macSSL ship under permissive licences (each subproject defines its own); the website license page is specifically about the *browser*, which is GPLv2.
