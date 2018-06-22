Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.network "forwarded_port", guest:80, host:8080, auto_correct: true
  config.vm.network "forwarded_port", guest:443, host:4443, auto_correct: true
  # Ports for Mailserver
  config.vm.network "forwarded_port", guest:25, host:2500, auto_correct: true
  config.vm.network "forwarded_port", guest:110, host:1100, auto_correct: true
  config.vm.network "forwarded_port", guest:143, host:1430, auto_correct: true
  # Port for WebCit interface change to " guest:80, host:8080, " if no other Apache server is running/
  config.vm.network "forwarded_port", guest:21742, host:21742, auto_correct: true
  config.vm.synced_folder "/home/vazogg/Vagrant/Apache_Vagrant", "/var/sync/" 
  config.vm.hostname = "apache"
config.vm.provider "virtualbox" do |vb|
  vb.memory = "512" 
  vb.name = "apache"
end
config.vm.provision "shell", inline: <<-SHELL
  # Software installieren
  sudo apt-get -y install apache2
  sudo apt-get update
  sudo cp -r /var/sync/html /var/www/
SHELL
end