# Holbreich RPM Repository

This repository hosts RPM packages published by [Alexander Holbreich](https://alexander.holbreich.org/) and serves them via GitHub Pages.

Repository URL:

- <https://aholbreich.github.io/rpm-repo/>

## Purpose

This is a simple personal RPM repository for distributing packages such as `adr-tool`.

The repository contains:

- RPM package files
- generated `repodata/` metadata for DNF/YUM clients
- repository documentation

## Supported clients

This repository is intended for RPM-based systems such as:

- Fedora
- Red Hat Enterprise Linux
- CentOS
- compatible distributions using `dnf` or `yum`

## Installation

Create a repo file on your system:

```bash
echo '[Holbreich]
name=Holbreich Repository
baseurl=https://aholbreich.github.io/rpm-repo/
enabled=1
gpgcheck=0' | sudo tee /etc/yum.repos.d/holbreich.repo
```

Then install packages as usual, for example:

```bash
sudo dnf install adr-tool
```

## Trust model

At the moment this repository does **not** publish signed RPM packages or signed repository metadata.

That is why the example configuration currently uses:

```ini
gpgcheck=0
```

This is acceptable for a personal repository if you understand the trade-off, but it is weaker than a properly signed RPM repository.

Planned future improvement:

- package signing with a dedicated RPM signing key
- optional repository metadata signing later

## Available packages

Currently published packages:

- `adr-tool`

Published RPMs currently present in this repository:

- `adr-tool-0.0.2-1.noarch.rpm`
- `adr-tool-0.0.2-19.7c50d5f.noarch.rpm`
- `adr-tool-0.1.1-12.c500828.noarch.rpm`
- `adr-tool-0.2.2-0.161b501.noarch.rpm`
- `adr-tool-0.2.2-3.aa0cf84.noarch.rpm`
- `adr-tool-0.3.0-1.2e9243a.noarch.rpm`
- `adr-tool-0.3.0-2.9526c67.noarch.rpm`
- `adr-tool-0.3.1-1.637231a.noarch.rpm`
- `adr-tool-0.3.3-1.9f16f89.noarch.rpm`
- `adr-tool-0.3.4-1.f555afc.noarch.rpm`
- `adr-tool-0.3.5-1.30b0000.noarch.rpm`
- `adr-tool-0.4.0-0.6904ff3.noarch.rpm`

## How it is maintained

Repository metadata is generated with `createrepo_c`.

A GitHub Actions workflow updates `repodata/` when:

- new RPM files are pushed
- the repository update workflow itself changes

That keeps the repository usable by DNF/YUM clients without having to regenerate metadata manually for unrelated edits.

## Development / maintenance notes

If you update this repository manually, regenerate metadata with:

```bash
createrepo_c --update .
```

## Troubleshooting

Refresh local package metadata if needed:

```bash
sudo dnf clean all
sudo dnf makecache
```

Inspect repository configuration:

```bash
sudo dnf repolist
```

If package installation fails, verify that:

- the repo file exists in `/etc/yum.repos.d/`
- the repository URL is reachable
- your local cache is up to date

## Related projects

- `adr-tool`: <https://github.com/aholbreich/adr-tool>
