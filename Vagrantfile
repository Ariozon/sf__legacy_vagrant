Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.network "private_network", type: "dhcp"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
  end
  config.vm.provision "shell", inline: <<-SHELL
    # Add PostgreSQL 8.4 repository
    sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" >> /etc/apt/sources.list.d/pgdg.list'
    wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

    # Update package lists
    sudo apt-get update

    # Install PostgreSQL 8.4 and its dependencies
    sudo apt-get install -y postgresql-8.4

    # Configure PostgreSQL to allow connections from host machine
    echo "host all all 0.0.0.0/0 md5" | sudo tee -a /etc/postgresql/8.4/main/pg_hba.conf
    echo "listen_addresses = '*'" | sudo tee -a /etc/postgresql/8.4/main/postgresql.conf

    # Restart PostgreSQL for changes to take effect
    sudo service postgresql restart

    # Check PostgreSQL version
    psql --version
  SHELL
end
