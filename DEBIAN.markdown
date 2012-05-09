Building Debian package of apitrace
===================================

Obviously, you will need the Debian development tools (dpkg-dev).

To build a debian package you should

 * check out apitrace from git

   git clone git://github.com/apitrace/apitrace.git

 * check out the debian files

   cd apitrace
   git checkout -b debian master
   git pull -f git://github.com/hramrach/apitrace.git debian
   git rebase master

 * make a source tarball

    debian/rules tarball

  The tarball is created in parent directory so that dpkg-buildpackage finds it.
  May overwrite existing apitrace_0.orig tarball.

 * build package

    dpkg-buildpackage

 * (on 64bit) build 32bit package

    extract the just created source package in a 32bit chroot (using eg. schroot)

    cd <your chroot>
    dpkg-source -x <wherever you built the package>/apitrace_0-<some junk>.dsc
    <chroot to your chroot>
    cd apitrace-0
    dpkg-buildpackage -b




