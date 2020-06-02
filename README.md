# raspberry-pi
# 1. Descargar e instalar raspbian en la SD
* Raspbian: https://downloads.raspberrypi.org/raspbian_lite_latest
* Etcher: (para escribir la SD) https://etcher.io/
* Instalar imagen en la SD

# 2. General settings
(to complete)

* set root password
* set sshd

# 3. Instalar paquetes necesarios

apt-get install -y \
     apt-transport-https \
     ca-certificates \
     curl \
     gnupg2 \
     software-properties-common \
     vim \
     fail2ban \
     ntfs-3g \ 
     glances \
     tmux
 
# 4. Instalar firmas GPG del repo de Docker
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88

# 5. Agregar Docker
echo "deb [arch=armhf] https://download.docker.com/linux/debian \
     $(lsb_release -cs) stable" | \
    sudo tee /etc/apt/sources.list.d/docker.list
    
apt-get update && sudo apt-get install -y docker-ce docker-compose

usermod -a -G docker pi

