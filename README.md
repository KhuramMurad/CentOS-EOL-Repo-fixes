CentOS 8 Repo Update Script 🚀
Overview
This project contains a bash script designed to update CentOS 8 repository configurations to the CentOS Vault URLs, ensuring your system remains up-to-date even after CentOS 8 has reached End of Life (EOL). The script also backs up your existing .repo files before making any changes.

Features ✨
Automatic Backup: Creates a timestamped backup directory and moves all existing .repo files into it.
Repository Update: Replaces the CentOS-Linux-BaseOS.repo file with an updated version pointing to the CentOS Vault URLs.
Easy to Use: Simply run the script with sudo and let it handle everything.
Script Details 📝
bash
Copy code
#!/bin/bash

BACKUP_DIR="/etc/yum.repos.d/backup_$(date +%F_%T)"
mkdir -p "$BACKUP_DIR"
mv /etc/yum.repos.d/*.repo "$BACKUP_DIR"

cat <<EOL > /etc/yum.repos.d/CentOS-Linux-BaseOS.repo
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
EOL

echo "Backup created in: $BACKUP_DIR"
echo "CentOS-Linux-BaseOS.repo updated successfully!"
How to Use 🛠️
Clone the Repository:

bash
Copy code
git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name
Make the Script Executable:

bash
Copy code
chmod +x update_repos.sh
Run the Script with sudo:

bash
Copy code
sudo ./update_repos.sh
Prerequisites 📋
CentOS 8 installed on your system.
Root privileges (use sudo to execute the script).
Contributing 🤝
Feel free to contribute to this project by submitting issues or pull requests. All contributions are welcome!

License 📄
This project is licensed under the MIT License. See the LICENSE file for more details.
