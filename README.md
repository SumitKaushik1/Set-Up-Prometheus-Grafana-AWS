# Set-Up-Prometheus-Grafana-AWS


## Step-by-Step Guide

### 1. Open AWS Account
- Log in to your AWS account.

### 2. Create an EC2 Instance for Prometheus
- Launch a new EC2 instance.
- Name the instance: **Prometheus Server**.
- Select the **Ubuntu operating system**.

### 3. Configure Network Settings
- In the network settings, check the boxes to:
  - Allow **HTTP traffic** from the internet.
  - Allow **HTTPS traffic** from the internet.

### 4. Edit Inbound Traffic Rules
- Add the following new security groups:

#### Prometheus
- Port number: **9090**
- Name: **prometheus**

#### Grafana
- Port number: **3000**
- Name: **grafana**

#### Node Exporter
- Port number: **9100**
- Name: **node-exporter**
<br>

- For all new security groups, set the source to **0.0.0.0/0**.

### 5. Launch a New Target Instance for Monitoring
- Launch a new EC2 instance.
- Use the **Ubuntu operating system**.
- In the network settings, edit the settings:
- Configure the **inbound traffic rule** as needed for monitoring purposes.
 #### Node Exporter
- Port number: **9100**
- Name: **node-exporter**

## Notes
- Ensure that all configurations comply with your security policies and best practices.
- Adjust security group settings as necessary for your specific use case.

next we will see in the nexr videi
