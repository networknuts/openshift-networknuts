
# Openshift Local Setup

This documentation is based on the Openshift Local installation by Network Nuts

## Prerequisites:
1. RHEL8 or RHEL9 Virtual Machine
2. Minimum 4 CPU & 9 GB RAM
3. 32 GB Disk Space in /home


## 1. Install Dependencies

Install Network Manager, Libvirt, Qemu

```bash
  yum install NetworkManager libvirt qemu-kvm -y
```

## 2. Download Openshift Packages

Navigate to https://console.redhat.com/openshift/create/local and download the tar file and the pull secret

## 3. Extract and Copy crc binary

```bash
tar -xvf crc-linux-amd64.tar.xz 
cp crc-linux-amd64/crc /usr/local/bin
chmod +x /usr/local/bin/crc
```
## 4. Set Openshift Local Settings

```bash
crc config set consent-telemetry no
```

## 5. Optional - Configure CPU and Memory

```bash
crc config set cpus 6
crc config set memory 12
```

## 6. Setup Openshift Local

```bash
crc setup 
```

## 7. Start Openshift Local

```bash
crc start -p pull-secret.txt
```
