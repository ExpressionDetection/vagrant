Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/bionic64"

  config.vm.provider "virtualbox" do |vb|
    # vb.gui = true
    vb.memory = 8192
    vb.cpus = 4
  end

  config.vm.boot_timeout = 9999999999

  # require plugin https://github.com/leighmcculloch/vagrant-docker-compose
  config.vagrant.plugins = "vagrant-docker-compose"

  # Install Docker
  config.vm.provision "docker"

  # Install Docker Compose
  config.vm.provision :docker_compose
  
  # Setup root user and SSH key
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update -y
    apt-get upgrade -y
    apt-get autoremove -y

    # Set SSH Key
    echo -e "\n\n\n" | ssh-keygen -t ed25519 -C "vm key"

    # Set Root password for local development
    # https://stackoverflow.com/questions/25758737/vagrant-login-as-root-by-default
    echo -e "vagrant\nvagrant" | passwd root
    echo "PermitRootLogin yes" >> /etc/ssh/sshd_config
    sed -in 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config
    service ssh restart

    echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf && sudo sysctl -p
    sudo mkdir -p /projects
  SHELL

  # Map VM projects folder to a local user folder at host machine
  config.vm.synced_folder "~/ExpressionDetection", "/projects"

  # Port forwarding
  config.vm.network "forwarded_port", guest: 3000, host: 3000 # chrome-extension frontend
  config.vm.network "forwarded_port", guest: 50051, host: 50051 # model1 gRPC api
  config.vm.network "forwarded_port", guest: 6969, host: 6969 # gRPC explorer web app

  # Login as root when doing vagrant ssh
  if ARGV[0]=='ssh'
    config.ssh.username = 'root'
    config.ssh.password = 'vagrant'
  end
end