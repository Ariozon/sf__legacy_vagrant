#vagrant with virtualbox on ubutu with GCP

Vagrant.configure("2") do |config|
  config.vm.provider :google do |google, override|
    google.google_project_id = "mist-testy-1234567"
    google.image_family = "ubuntu-1804-lts"
    google.zone = "us-central1-a"
    google.machine_type = "n1-standard-2"
    google.private_key_path = "~/.ssh/id_rsa"
  end

  config.vm.provision :shell, inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y postgresql-8.4
  SHELL

  config.vm.box = "google/gce"

end
