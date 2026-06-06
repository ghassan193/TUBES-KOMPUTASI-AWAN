Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-22.04"

  # Konfigurasi 3 VM: Database, Backend, Frontend
  [
    ["database", "192.168.56.21", "VM-Database-Maknyuso"],
    ["backend", "192.168.56.20", "VM-Backend-Maknyuso"],
    ["frontend", "192.168.56.22", "VM-Frontend-Maknyuso"]
  ].each do |name, ip, vname|
    config.vm.define name do |machine|
      machine.vm.hostname = name
      machine.vm.network "private_network", ip: ip
      machine.vm.provider "virtualbox" do |vb|
        vb.name = vname
        vb.memory = "1024"
        vb.cpus = 1
      end

      # EKSEKUSI LOKAL: Setiap VM menginstal Ansible dan menjalankan tugasnya sendiri
      machine.vm.provision "shell", inline: <<-SHELL
        echo "Menginstal Ansible pada #{name}..."
        export DEBIAN_FRONTEND=noninteractive
        sudo apt-get update -y
        sudo apt-get install -y ansible
        
        echo "Mengeksekusi Playbook untuk #{name}..."
        sudo ansible-playbook /vagrant/playbook.yml -c local -e "target_node=#{name}"
      SHELL
    end
  end
end