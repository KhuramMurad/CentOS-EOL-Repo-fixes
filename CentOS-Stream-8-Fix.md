

First, let's create a new markdown file for CentOS Stream 8. Here's the structure:

markdownCopy# CentOS Stream 8 Repository Fixes

This guide provides the repository configurations to fix EOL (End of Life) issues with CentOS Stream 8.

## Quick Fix

1. Backup existing repo files:
```bash
cd /etc/yum.repos.d/
mkdir backup
mv *.repo backup/

Create new repository files:

CentOS-BaseOS.repo
iniCopy[baseos]
name=CentOS Stream 8 - BaseOS
baseurl=https://vault.centos.org/8-stream/BaseOS/$basearch/os/
gpgcheck=1
enabled=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-centosofficial
metadata_expire=6h
CentOS-EPEL.repo
iniCopy[epel]
name=Extra Packages for Enterprise Linux 8 - $basearch
baseurl=https://dl.fedoraproject.org/pub/epel/8/Everything/$basearch/
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-8

[epel-debuginfo]
name=Extra Packages for Enterprise Linux 8 - $basearch - Debug
baseurl=https://dl.fedoraproject.org/pub/epel/8/Everything/$basearch/debug/
enabled=0
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-8

[epel-source]
name=Extra Packages for Enterprise Linux 8 - $basearch - Source
baseurl=https://dl.fedoraproject.org/pub/epel/8/Everything/source/tree/
enabled=0
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-8

Update the system:

bashCopyyum clean all
yum makecache
yum update
Alternative Mirrors
If the default mirrors are slow or unavailable, you can try these alternative mirrors:
For BaseOS:
iniCopy#baseurl=https://vault.epel.cloud/centos/8-stream/BaseOS/$basearch/os/
#baseurl=https://archive.kernel.org/centos-vault/8-stream/BaseOS/$basearch/os/
For EPEL:
iniCopy#baseurl=https://mirror.umd.edu/fedora/epel/8/Everything/$basearch/
#baseurl=https://mirror.dal.ca/epel/8/Everything/$basearch/
Verification
To verify that repositories are working correctly:
bashCopyyum repolist
Copy
To add this to your GitHub repository:

1. Clone your repository locally:
```bash
git clone https://github.com/KhuramMurad/CentOS-EOL-Repo-fixes.git
cd CentOS-EOL-Repo-fixes
