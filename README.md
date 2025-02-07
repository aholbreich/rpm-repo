# Overview

This is the home of RPM Repository.
The repository as home for tools provided by [Alexander Holbreich](https://alexander.holbreich.org/), [@aHolbreich](https://github.com/aholbreich)

## Repository Location 

* https://aholbreich.github.io/rpm-repo/

## Installation (Fedora, CentOS, RedHat...)

run the following to register the repository

```bash
echo '[Holbreich]
name=aHolbreich Repository
baseurl=https://aholbreich.github.io/rpm-repo/
enabled=1
gpgcheck=0' | sudo tee /etc/yum.repos.d/aHolbreich.repo

```
## Packages
 TODO