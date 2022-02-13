# set up the default terminal
ENV["TERM"]="linux"

Vagrant.configure("2") do |config|

  # Use opensuse machine image
  config.vm.box = "opensuse/Leap-15.2.x86_64"
  config.vm.box_version = "15.2.31.584"

  # Kubernetes API Access
  config.vm.network "forwarded_port", guest: 6443, host: 6443

  # Expose NodePort ports
  for p in 30000..30100
    config.vm.network "forwarded_port", guest: p, host: p, protocol: "tcp"
    end

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.56.10"

  # Define the resources for the virtualbox
  config.vm.provider "virtualbox" do |vb|
    vb.cpus = 2
    vb.memory = "4096"
    vb.customize ["modifyvm", :id, "--ioapic", "on"]
  end
end
