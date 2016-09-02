Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/trusty64"

  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.synced_folder "exercise", "/home/vagrant/exercise"

  # Fix TTY error message
  config.vm.provision "fix-no-tty", type: "shell" do |s|
     s.privileged = false
     s.inline = "sudo sed -i '/tty/!s/mesg n/tty -s \\&\\& mesg n/' /root/.profile"
  end

  config.vm.provision "shell", inline: <<-SHELL
     sudo apt-get update
     sudo apt-get install -y php5
     echo -e "\n--- Setting web server document root to exercise directory ---\n"
     rm -rf /var/www/html
     ln -fs /vagrant/exercise /var/www/html
   SHELL
end
