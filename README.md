# How to Configure a Repo in CentOS?

Before modifying the repository files, ensure you have appropriate backup procedures in place:

```bash
sudo cp /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
```

## Editing Repository Files

To modify the repository sources, open the respective repository configuration file (**/etc/yum.repos.d/CentOS-Base.repo**) using your preferred text editor:

```bash
sudo vi /etc/yum.repos.d/CentOS-Base.repo
```

Replace the content in the file with the configurations listed below based on your CentOS version.

## CentOS 7

To configure the working repositories for CentOS 7, add the following to your **/etc/yum.repos.d/CentOS-Base.repo** file:

```ini
[base]
name=CentOS-$releasever - Base
baseurl=https://vault.centos.org/7.9.2009/os/$basearch/
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
enabled=1

[updates]
name=CentOS-$releasever - Updates
baseurl=https://vault.centos.org/7.9.2009/updates/$basearch/
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
enabled=1

[extras]
name=CentOS-$releasever - Extras
baseurl=https://vault.centos.org/7.9.2009/extras/$basearch/
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
enabled=1

[centosplus]
name=CentOS-$releasever - CentOSPlus
baseurl=https://vault.centos.org/7.9.2009/centosplus/$basearch/
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
enabled=0
```

## CentOS 8

To configure the working repositories for CentOS 8, add the following to your **/etc/yum.repos.d/CentOS-Base.repo** file:

```ini
[baseos]
name=CentOS Linux $releasever - BaseOS
baseurl=https://vault.centos.org/$contentdir/$releasever/BaseOS/$basearch/os/
gpgcheck=1
enabled=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-centosofficial

[appstream]
name=CentOS Linux $releasever - AppStream
baseurl=https://vault.centos.org/$contentdir/$releasever/AppStream/$basearch/os/
gpgcheck=1
enabled=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-centosofficial

[extras]
name=CentOS Linux $releasever - Extras
baseurl=https://vault.centos.org/$contentdir/$releasever/extras/$basearch/os/
gpgcheck=1
enabled=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-centosofficial

[centosplus]
name=CentOS Linux $releasever - Plus
baseurl=https://vault.centos.org/$contentdir/$releasever/centosplus/$basearch/os/
gpgcheck=1
enabled=0
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-centosofficial
```

## Important Notes

Proper repository configuration requires matching the repository URLs with your installed CentOS version. Over time, as new CentOS versions are released, older versions are moved to archive storage. The CentOS Vault serves as a centralized archive for these historical releases, storing all packages and updates for legacy versions. This guide provides verified repository configurations for both CentOS 7 and CentOS 8, helping you maintain long-term system stability and package accessibility, even for end-of-life releases.
