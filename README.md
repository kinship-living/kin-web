# kin-web

KIN's two web sites built for kin-devel, for testing and development, served by GitHub Pages:

| URL | What |
| --- | --- |
| https://kinship-living.github.io/kin-web/vouch/v#&lt;token&gt; | the vouch form, against kin-devel |
| https://kinship-living.github.io/kin-web/vouch/w#&lt;token&gt; | the withdrawal page |
| https://kinship-living.github.io/kin-web/app/ | app.kinship.living's pages |

Everything here is generated. The sources, tests and build live in the private kin-baas repository (`web/`), and
kin-baas's `web/publish.sh` replaces this repository's contents through a pull request. `SOURCE` names the
kin-baas commit the site was built from. Test data only; production is served from Cloudflare Pages.
