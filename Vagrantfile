Vagrant.configure("2") do |config|
  config.vm.define "ansible" do |ansible|
  ansible.vm.hostname = "ansible"
  ansible.vm.box = "centos/7"
  ansible.vm.network "public_network" , type: "static", ip: "192.168.1.105"
  ansible.vm.provision "shell", inline:
  "sudo yum update -y
  sudo yum install vim -y
  sudo yum install epel-release -y 
  sudo yum install python ansible -y
  sudo yum install git -y
  sudo cp /vagrant/id_rsa /home/vagrant/.ssh/
  sudo cp /vagrant/id_rsa.pub /home/vagrant/.ssh/
  sudo cp /vagrant/sshd_config /etc/ssh/sshd_config
  sudo chown vagrant:vagrant /etc/ssh/sshd_config
  eval $(ssh-agent -s)
  sudo ssh-add /home/vagrant/.ssh/id_rsa
  sudo systemctl restart sshd
  sudo mkdir /ansible/
  git clone https://github.com/cesar-deploy/ansible-wordpress-mysql /ansible/"
  

  end
  config.vm.define "webserver" do |webserver|
    webserver.vm.define "webserver" 
    webserver.vm.hostname = "webserver"
    webserver.vm.box = "ubuntu/bionic64"
    webserver.vm.network "public_network" , type: "static", ip: "192.168.1.106"
    webserver.vm.provision "shell", inline:
    "sudo apt-get update -y
     sudo cp /vagrant/id_rsa /home/vagrant/.ssh/
     sudo cp /vagrant/id_rsa.pub /home/vagrant/.ssh/
     sudo cp /vagrant/sshd_config /etc/ssh/sshd_config
     sudo chown vagrant:vagrant /etc/ssh/sshd_config
     eval $(ssh-agent -s)
     sudo ssh-add /home/vagrant/.ssh/id_rsa
     sudo systemctl restart sshd"

   
  end
  config.vm.define "mysql" do |mysql|
    mysql.vm.hostname = "mysql"
    mysql.vm.box = "ubuntu/bionic64"
    mysql.vm.network "public_network", type: "static", ip: "192.168.1.107"
    mysql.vm.provision "shell", inline:
    "sudo apt-get update -y
     sudo cp /vagrant/id_rsa /home/vagrant/.ssh/
     sudo cp /vagrant/id_rsa.pub /home/vagrant/.ssh/
     sudo cp /vagrant/sshd_config /etc/ssh/sshd_config
     sudo chown vagrant:vagrant /etc/ssh/sshd_config
     eval $(ssh-agent -s)
     sudo ssh-add /home/vagrant/.ssh/id_rsa
     sudo systemctl restart sshd"
  end  
end
