Vagrant.configure("2") do |config|
    # Usar la caja base de Ubuntu 18.04
    config.vm.box = "ubuntu/bionic64"
  
    # Asignar 512MB de RAM y 1 CPU
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  
    # Configuración de red (opcional, puedes usar "private_network" si es necesario)
    config.vm.network "private_network", type: "dhcp"
  
    # Compartir el directorio local con la VM
    config.vm.synced_folder "./web_pages", "/var/www/html"
  
    # Configurar el servidor web Apache
    config.vm.provision "shell", inline: <<-SHELL
      # Actualizar el sistema
      sudo apt-get update
      sudo apt-get upgrade -y
  
      # Instalar Apache
      sudo apt-get install -y apache2
  
      # Habilitar Apache para iniciar en el arranque
      sudo systemctl enable apache2
  
      # Reiniciar el servidor Apache
      sudo systemctl restart apache2
    SHELL
  end
  