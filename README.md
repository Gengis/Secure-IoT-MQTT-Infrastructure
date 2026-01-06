# Secure-IoT-MQTT-Infrastructure
# 🛡️ Secure IoT Infrastructure with MQTT & TLS

## 📋 Project Overview
This project demonstrates the design and implementation of a hardened IoT communication architecture using the MQTT protocol. The objective was to secure critical industrial telemetry against interception and unauthorized access by implementing strict Authentication, Authorization (ACLs), and Transport Layer Security (TLS/SSL).

## 🚀 Key Features
* **Custom PKI Implementation:** Generated a private Certificate Authority (CA) to sign server and client certificates using OpenSSL.
* **Encrypted Transport:** Secured MQTT traffic over port 8883 using TLS 1.2 to prevent Man-in-the-Middle (MitM) attacks.
* **Granular Access Control (ACLs):** Implemented Principle of Least Privilege. Sensors can only *publish* to specific topics, and monitoring panels can only *subscribe*.
* **Authentication:** Removed anonymous access; enforced strict username/password policies.

## 🛠️ Technology Stack
* **OS:** Kali Linux / Debian
* **Broker:** Eclipse Mosquitto
* **Security:** OpenSSL (PKI Management)
* **Tools:** Mosquitto_pub/sub clients

## ⚙️ Configuration Snippets

### 1. `mosquitto.conf` (Hardened)
```conf
listener 8883
cafile /etc/mosquitto/certs/ca.crt
certfile /etc/mosquitto/certs/server.crt
keyfile /etc/mosquitto/certs/server.key
require_certificate false
allow_anonymous false
password_file /etc/mosquitto/passwd
acl_file /etc/mosquitto/aclfile
