# Odoo Installation Script (Version Agnostic)

This script automates the installation and configuration of **Odoo** on an **Ubuntu** server. It supports installing **any version** of Odoo by specifying the desired version in the script or as a variable.

---

## 📁 Files & Directories

- **Installation Script**: `install_odoo.sh`
- **Odoo User**: `odoo`
- **Installation Path**: `/odoo`
- **Custom Addons Path**: `/odoo/custom/addons`
- **Configuration File**: `/etc/odoo-server.conf`
- **Log File**: `/var/log/odoo/odoo-server.log`
- **Service File**: `/etc/init.d/odoo-server`

---

## 🧰 What the Script Does

1. **System Update & Dependency Installation**
   - Installs Python 3, pip, PostgreSQL, wkhtmltopdf, and required packages.

2. **Create System User and Directories**
   - Adds a system user `odoo` (no shell login).
   - Creates base and custom addons directories.

3. **Clone the Odoo Source Code**
   - Clones the specific version (e.g. 15.0, 16.0, 17.0) from the official GitHub repository.

4. **Python Virtual Environment Setup**
   - Installs all necessary Python libraries via `pip`.

5. **PostgreSQL Setup**
   - Creates a PostgreSQL role named `odoo`.

6. **Create Odoo Configuration**
   - Generates `/etc/odoo-server.conf` with defined master password, ports, paths.

7. **Configure as a Linux Service**
   - Sets up Odoo as a `SysVinit` service via `/etc/init.d/odoo-server`.

8. **Enable and Start Service**
   - Ensures Odoo starts at boot and starts it immediately.

---

## ⚙️ Default Configuration

- **Master Password**: `XXXXXXXXXXXX` (updateable in the script or in `/etc/odoo-server.conf`)
- **Port**: `8069`
- **Addons Path**:
  - `/odoo/odoo-server/addons`
  - `/odoo/custom/addons`

---

## 📌 Version Selection

You can change the Odoo version to install by modifying the following line in the script:

```
OE_VERSION="16.0"  # Change this to 15.0, 17.0, etc.
```
## 🚀 How to Use
Make the script executable:
```
chmod +x install_odoo.sh
```
Run the script:


```
sudo ./install_odoo.sh 
```
Access Odoo in your browser:

```
http://<your-server-ip>:8069
```
## 🔄 Service Commands
```
sudo service odoo-server start     # Start Odoo
sudo service odoo-server stop      # Stop Odoo
sudo service odoo-server restart   # Restart Odoo
sudo service odoo-server status    # Check status
```
## 📑 Logs & Config

Log File: ``` /var/log/odoo/odoo-server.log ```

Configuration: ``` /etc/odoo-server.conf ```

## PS

if the current odoo installation does not work you may change this line :
```
sudo -H pip3 install -r https://github.com/odoo/odoo/raw/${OE_VERSION}/requirements.txt

```
with this line:
```
sudo -H pip3 install -r https://raw.githubusercontent.com/MedMokhtarAmmar/odoo_install/main/requirements.txt
```
