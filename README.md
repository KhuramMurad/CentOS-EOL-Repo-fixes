CentOS 8 Repo Update Script 🚀
Overview
This project contains a bash script designed to update CentOS 8 repository configurations to the CentOS Vault URLs, ensuring your system remains up-to-date even after CentOS 8 has reached End of Life (EOL). The script also backs up your existing .repo files before making any changes.

Features ✨
Automatic Backup: Creates a timestamped backup directory and moves all existing .repo files into it.
Repository Update: Replaces the CentOS-Linux-BaseOS.repo file with an updated version pointing to the CentOS Vault URLs.
Easy to Use: Simply run the script with sudo and let it handle everything.
Script Details 📝

#!/bin/bash

# Create a backup directory in /etc/yum.repos.d/
BACKUP_DIR="/etc/yum.repos.d/backup-$(date +%Y%m%d%H%M%S)"
mkdir -p "$BACKUP_DIR"
echo "Backup directory created successfully: $BACKUP_DIR"

# Move all files to the backup directory
mv /etc/yum.repos.d/* "$BACKUP_DIR/"
echo "Files moved to backup directory successfully"

# Create a new CentOS-Linux-BaseOs.repo file with the updated contents
cat <<EOF > /etc/yum.repos.d/CentOS-Linux-BaseOs.repo
[BaseOS]
name=CentOS Linux \$releasever - BaseOS
baseurl=http://vault.centos.org/8.5.2111/BaseOS/\$basearch/os/
gpgcheck=1
enabled=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-centosofficial

[AppStream]
name=CentOS Linux \$releasever - AppStream
baseurl=http://vault.centos.org/8.5.2111/AppStream/\$basearch/os/
gpgcheck=1
enabled=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-centosofficial

[Extras]
name=CentOS Linux \$releasever - Extras
baseurl=http://vault.centos.org/8.5.2111/Extras/\$basearch/os/
gpgcheck=1
enabled=0
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-centosofficial
EOF
echo "CentOS-Linux-BaseOs.repo file updated successfully"
echo "Backup created in: $BACKUP_DIR"
echo "CentOS-Linux-BaseOS.repo updated successfully!"



How to Use 🛠️

Clone the Repository:
git clone [https://github.com/yourusername/your-repo-name.git](https://github.com/KhuramMurad/CentOS-EOL-Repo-fixes.git)

cd your-repo-name

Make the Script Executable:
chmod +x update_repos.sh

Run the Script with sudo:
sudo ./update_repos.sh

Prerequisites 📋
CentOS 8 installed on your system.
Root privileges (use sudo to execute the script).
Contributing 🤝
Feel free to contribute to this project by submitting issues or pull requests. All contributions are welcome!

License 📄
This project is licensed under the GPL License.
