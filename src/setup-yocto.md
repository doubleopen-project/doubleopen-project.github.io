# Setup Yocto

Double Open's layer, [`meta-doubleopen`](https://github.com/doubleopen-project/meta-doubleopen) is
used to create an [SPDX Document](https://spdx.github.io/spdx-spec/composition-of-an-SPDX-document/)
describing the image built with Yocto. The layer needs to be added to `conf/bblayers.conf` and
enabled with `INHERIT += "doubleopen"` in `conf/local.conf`.

After `meta-doubleopen` is added, `bitbake build <RECIPE>` produces SPDX Documents for all packages
in `<SPDX_DEPLOY_DIR>` (defaults to `/build/tmp/deploy/spdx/`) and the SPDX Document for the whole
image is saved to `DEPLOY_DIR_IMAGE`.
