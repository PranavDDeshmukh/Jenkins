
## Jenkins Installation

#### Prerequisites

![Screenshot 2024-12-10 121817](https://github.com/user-attachments/assets/da34b663-d46b-4027-8194-caf0a7c2c2e2)

````
sudo apt update
sudo apt install fontconfig openjdk-17-jre -y
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
````
- Then copy the public ip of your instance and hit the ip **13.126.152.219:8080**

![image](https://github.com/user-attachments/assets/26b01075-6662-4980-929a-1cae283738c3)

- then copy administrator password in this file **/var/lib/jenkins/secrets/initialAdminPassword**

![image](https://github.com/user-attachments/assets/1f59c0c2-2fce-4f53-b3ee-3d9b9c90428b)

