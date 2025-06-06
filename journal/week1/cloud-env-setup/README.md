# Cloud Environment SetUp

With our cloud environment already setup with a VPC, we spun up the rest of the resources we'd need for the bootcamp.


## Security Group Creation

- Set up **Security Group (SG)** 
  - **Rule 1**: Allows **RDP access only from my IP**.
  - **Rule 2**: Permits **all traffic** from devices on the network. 
  - **Rule 3**: Allows SSH access to devices on the network. 

## Key Creation
- Generated **key pairs**: `.pem` and `.ppk` for authentication.

## Servers Provisioning
We created the servers we would be using through the bootcamp. 

*Windows server* (publicly accessible) expected to be the main host, while others are for testing.


### Windows Server Deployment
- Launched **Windows Server** (Windows Base 2025).
- Assigned **PEM key** 
- Created **private NIC**, resulting in:
  - **Public NIC**
  - **Private NIC**
- Attached **Private NIC** to Windows server.

- **RDP login steps**:
  1. Used **PEM key** to **decrypt the password**.
  2. Logged in with the decrypted **password**.
  3. **Windows username:** `Administrator` (expected by default for Windows instances).

### Ubuntu Server Deployment
- Launched **Ubuntu test server**.
- Attached **Private NIC**.
- Configured **PPK key** for authentication.
- Used **Pageant** to SSH into the server (Pageant forwards the key for authentication, avoiding password entry).
- Used **PuTTY** to authenticate.
- **Ubuntu username:** `ubuntu` (expected by default for Ubuntu instances).

### RedHat Server Deployment
- Launched **RedHat instance**.
- Attached **Private NIC**.
- **RedHat username:** `ec2-user` (default username for RedHat instances).

## Elastic IP Assignment
- Created **Elastic IP addresses** for each server to ensure **static IP allocation** during the bootcamp.


