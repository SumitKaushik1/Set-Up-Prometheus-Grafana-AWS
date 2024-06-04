# Set-Up-Prometheus-Grafana-AWS


## Step-by-Step Guide To Configure AWS Instance

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

or 
- changes can be applied on the running instance(portfolio1 or prometheus server)
 - change only the security group inbound traffic rule and add 
     #### Node Exporter
     - Port number: **9100**
     - Name: **node-exporter**  
## Notes
- Ensure that all configurations comply with your security policies and best practices.
- Adjust security group settings as necessary for your specific use case.

_____________________________________________________________________________________________________
## Install the Prometheus and Graphana on AWS Instance
### First, you connected to the prometheus server AWS instance. Then, you executed the following commands:

````sh 
 sudo su
````
### This command switches the user to the root user and These commands navigate to the root directory.
 
  ``````sh
    cd ..
    cd ..

  ``````
###  This command clones the Prometheus_Monitoring repository from GitHub.

  ``````sh
         git clone https://github.com/vipinkumar1234/Prometheus_Monitoring.git
  ``````

###  This command moves into the Prometheus_Monitoring directory.
``````sh
  cd Prometheus_Monitoring
``````
###  This command runs the bash file to configure and install Prometheus, and then starts the Prometheus service.
``````sh
 ./install-prometheus.sh
``````

###  Next, you opened another tab and typed:
``````sh
3.111.36.210:9090/targets
``````
###  This command checks if the Prometheus service is running by accessing the targets page on the specified IP address and port.
### You explained that Prometheus is an API (Application Programming Interface), and Grafana interacts with the Prometheus API to create dashboards.
###  To install Grafana, you can use the following commands provided by ChatGPT:
``````sh
sudo apt-get update
sudo apt-get install -y software-properties-common
sudo apt-get install -y apt-transport-https
sudo apt-get install -y wget
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
sudo apt-get update
sudo apt-get install grafana
sudo systemctl start grafana-server
sudo systemctl enable grafana-server
````````
###  If the above commands give an error, you can apply these commands:
````sh
sudo nano /etc/apt/sources.list.d/grafana.list
````
###  Comment out the previous line and add the following text:
````sh
# Remove the beta version repository
deb [signed-by=/etc/apt/keyrings/grafana.gpg] https://apt.grafana.com stable main
# Remove the duplicate stable version repository
# deb https://apt.grafana.com stable main
# Keep only one stable version repository entry
deb https://packages.grafana.com/oss/deb stable main
`````
###  Save the file.
`````sh
sudo rm /etc/apt/keyrings/grafana.gpg
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
sudo apt-get update
sudo apt-get install grafana
sudo systemctl start grafana-server
sudo systemctl enable grafana-server
sudo systemctl status grafana-server
``````
###  You mentioned that even after executing these commands, the Grafana service might not start, and the status shows it as dead and inactive.



