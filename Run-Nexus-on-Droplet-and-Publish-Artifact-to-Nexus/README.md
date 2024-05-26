# Run Nexus on Droplet and Publish Artifact to Nexus

This project demonstrates setting up a Nexus repository on a DigitalOcean droplet and publishing Java artifacts to the Nexus repository. Below are the detailed steps and commands used to achieve this setup.

## Tech Stack
- DigitalOcean Droplet
- Nexus Repository Manager
- Java (OpenJDK 8)
- Gradle
- Maven
- SSH

## Project Steps

### 1. Create and Access DigitalOcean Droplet
```sh
# Create a droplet on DigitalOcean
# SSH into the droplet from the terminal
ssh root@<your_droplet_ip>
```
![Alt text](./images/screenshot.png)


### 2. Update Dependencies and Install Java
```sh
# Update all dependencies
apt update

# Install Java
apt install openjdk-8-jre-headless

# Install additional network tools
apt install net-tools
```
![Alt text](./images/screenshot.png)

### 3. Download and Extract Nexus
```sh
# Change directory to /opt
cd /opt

# Download Nexus file
wget https://download.sonatype.com/nexus/3/nexus-3.68.1-02-java8-mac.tgz

# Extract the Nexus tar file
tar -zxvf nexus-3.68.1-02-java8-mac.tgz
```
![Alt text](./images/screenshot.png)


### 4. Configure Nexus User
```sh
# Add a new user for Nexus
adduser nexus

# Change ownership and group of the Nexus directories
chown -R nexus:nexus nexus-3.68.1-02
chown -R nexus:nexus sonatype-work
```
![Alt text](./images/screenshot.png)


### 5. Update Nexus Configuration
```sh
# Update Nexus to run as the Nexus user
vim nexus-3.68.1-02/bin/nexus.rc

# Add the following line
run_as_user="nexus"
```
![Alt text](./images/screenshot.png)


### 6. Start Nexus
```sh
# Switch to the Nexus user
su - nexus

# Start the Nexus application
/opt/nexus-3.68.1-02/bin/nexus start
```
![Alt text](./images/screenshot.png)


### 7. Verify Nexus Is Running
```sh
# Check the Nexus process and listen ports
ps aux | grep nexus
netstat -lnpt
```
Ensure Nexus is running on port `8081`.

![Alt text](./images/screenshot.png)


### 8. Configure and Publish Java Artifacts
```sh
# Edit the build.gradle file and the pom.xml file with the necessary configurations to publish Java artifacts to Nexus
# Note: Specific steps for editing these files are not included as they depend on the project requirements.
```

![Alt text](./images/screenshot.png)
