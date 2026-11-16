# kin-web

HUXLEY's web pages, built from kin-baas. Two deploys run from here:

| Folder | Served at | Built for | By |
| --- | --- | --- | --- |
| `site/` | https://kinship-living.github.io/kin-web/ | kin-devel | `pages`, GitHub Pages |
| `wordpress/friend-vouch/` | https://thehuxley.app/friend-vouch/ | kin-prod | `wordpress`, SFTP to the WordPress host |

| Address | What |
| --- | --- |
| https://thehuxley.app/friend-vouch/#&lt;token&gt; | the vouch form |
| https://thehuxley.app/friend-vouch/withdraw/#&lt;key&gt; | the withdrawal page |
| https://kinship-living.github.io/kin-web/vouch/#&lt;token&gt; | the vouch form, against kin-devel |
| https://kinship-living.github.io/kin-web/vouch/withdraw/#&lt;key&gt; | the withdrawal page, against kin-devel |
| https://kinship-living.github.io/kin-web/app/ | app.kinship.living's pages |

The vouch form on thehuxley.app is plain files in their own folder beside WordPress, never a WordPress page: the
WordPress pages run analytics, which could read a link's token and a friend's answers. The folder's `.htaccess` sets
the security headers and keeps WordPress's rewrites out of it. The `wordpress` workflow uploads into that folder
only, deletes nothing, and then checks what https://thehuxley.app/friend-vouch/ serves. It needs the secrets
`WORDPRESS_SFTP_HOST`, `WORDPRESS_SFTP_USER`, `WORDPRESS_SFTP_PASSWORD` and `WORDPRESS_SFTP_KNOWN_HOSTS`, and the
variable `WORDPRESS_SFTP_ROOT` (see the top of `.github/workflows/wordpress.yml`).

Everything here is generated. The sources, tests and build live in the private kin-baas repository (`web/`), and
kin-baas's `web/publish.sh` replaces this repository's contents through a pull request. `SOURCE` names the kin-baas
commit both were built from. `site/` holds test data only.
