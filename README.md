# app2unit for fedora

Fedora RPM packaging for [app2unit](https://github.com/Vladimir-csp/app2unit), a shell script that launches desktop entries and arbitrary commands as systemd user units.

## Installing from COPR

A prebuilt package is available from the `celestelove/app2unit` COPR repository. Enable it and install with dnf:

```sh
sudo dnf copr enable celestelove/app2unit
sudo dnf install app2unit
```

## Building from source

Install the build dependencies:

```sh
sudo dnf install rpm-build rpmdevtools scdoc gzip
```

Set up the rpmbuild tree and build:

```sh
rpmdev-setuptree
spectool -g -R app2unit.spec
rpmbuild -ba app2unit.spec
```

The built RPM will be in `~/rpmbuild/RPMS/noarch/`.

### Using mock

To build in a clean chroot instead:

```sh
spectool -g app2unit.spec
mock --buildsrpm --spec app2unit.spec --sources .
mock --rebuild ~/rpmbuild/SRPMS/app2unit-*.src.rpm
```

