OpenBSD httpd daemon
====================

The httpd daemon is an HTTP server with FastCGI and TLS support.

This repository mirrors the original httpd source tree from OpenBSD's
CVS and adds experimental branches on top.  It is **not** a portable
version and is only intended for OpenBSD.  Branches other than `main`
may contain highly experimental changes — do not use them in
production.

The authoritative source remains OpenBSD's CVS tree:

* https://cvsweb.openbsd.org/src/usr.sbin/httpd
* https://cvsweb.openbsd.org/src//regress/usr.sbin/httpd/

Branch layout
-------------

* **`main`** — a 1:1 mirror of the upstream CVS tree.  It is updated
  via periodic syncs and contains nothing that is not already in CVS.
  Never commit directly to this branch.

* **`devel`** — the integration branch for this repository.  It
  tracks `main` and adds Git-only material such as this README, the
  `regress/` harness, build helpers and other tooling that is useful
  during development but not (yet) part of upstream.  `devel` is
  rebased on top of `main` after every CVS sync.

* **Feature / bugfix branches** — all new work happens on dedicated
  topic branches forked from `devel`.  A branch lives until the change
  is either dropped or accepted upstream.

Upstream workflow
-----------------

Changes intended for OpenBSD follow the project's normal review
process:

1. Develop and test the change on a topic branch.
2. Generate a patch against the CVS tree and send it to
   <tech@openbsd.org> (or the appropriate developer) for review.
3. Iterate on feedback until the change is committed to CVS by an
   OpenBSD developer.
4. The next CVS-to-Git sync brings the change into `main`; `devel` is
   then rebased on top, and the topic branch can be deleted.

This means that, from the perspective of this repository, an accepted
upstream change eventually "lands" in `main` via the sync rather than
through a Git merge.

Collaboration
-------------

Development happens primarily on the Gothub instance; the other two
locations are kept in sync:

* **Primary:** https://rsadowski.gothub.org/
* **Mirror:** https://codeberg.org/rsadowski/httpd
* **Mirror:** https://github.com/sizeofvoid/httpd

Patches and reviews are always welcome:

* For review targeting OpenBSD, send diffs to <tech@openbsd.org> -
  this is the canonical path and gets the broadest review.
* Pull requests against the Codeberg or GitHub mirrors are also
  welcome, in particular for repository-specific material (regress,
  tooling, README, experimental work).
* Bug reports and feature requests can be filed as issues on either
  Codeberg or GitHub. Please use issues only for actual bugs or
  concrete proposals and not for general OpenBSD support questions.
