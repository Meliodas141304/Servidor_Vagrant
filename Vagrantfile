Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64" # Usa Ubuntu 18.04
  config.vm.network "private_network", ip: "192.168.56.10" # IP estática
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "512"
    vb.cpus = 1
  end
  config.vm.synced_folder "./html", "/var/www/html" # Compartir carpeta local con Apache
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt update
    sudo apt install -y apache2
    sudo systemctl enable apache2
    sudo systemctl start apache2
    echo "<h1>Hola Mundo desde Apache en Vagrant</h1>" | sudo tee /var/www/html/index.html
  SHELL
end
