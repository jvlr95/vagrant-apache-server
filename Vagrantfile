Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"

  # Server Web Apache
  config.vm.define "web" do |web|
    web.vm.hostname = "server-web"
    web.vm.synced_folder "/mnt/samba-server/var/www/html/", "/var/www/html"
    web.vm.network "forwarded_port", guest: 80, host: 8090
    web.vm.network "private_network", ip: "192.168.1.105"

    # web.vm.provider "virtualbox" do |vb|
    #   vb.memory = "1024"
    #   vb.cpus = 1
    # end

    web.vm.provision "shell", inline: <<-EOF
      apt update
      apt install apache2 -y
      apt install vim -y
      apt upgrade -y
      systemctl enable --now apache2
    EOF
  end

  # Database server
  config.vm.define "data" do |data|
    data.vm.hostname = "data"
    data.vm.network "private_network", ip: "192.168.1.115"

    # data.vm.provider "virtualbox" do |vb|
    #   vb.memory = "2048"
    #   vb.cpus = 2
    # end

    data.vm.provision "shell", inline: <<-EOF
      apt update
      apt install vim -y
      apt install mariadb-server -y
      apt upgrade -y
      systemctl enable --now mariadb.service
      sed -i 's/# port = 3306/port = 3306/' /etc/mysql/mariadb.cnf
      sed -i 's/127.0.0.1/0.0.0.0/' /etc/mysql/mariadb.conf.d/50-server.cnf
      systemctl restart mariadb.service
    EOF
  end
end

