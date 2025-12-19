Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
    vb.cpus = 2
  end

  # Provision כאן מחוץ ל-vb
  config.vm.provision "shell", inline: <<-SHELL
    set -e

    # --- Update + utilities ---
    sudo apt-get update
    sudo apt-get install -y apt-transport-https ca-certificates curl gnupg lsb-release software-properties-common

    # --- Install Docker ---
    sudo apt-get install -y docker.io
    sudo usermod -aG docker vagrant
    sudo systemctl enable docker
    sudo systemctl start docker

    # --- Install kubectl ---
    curl -fsSL https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo gpg --dearmor -o /usr/share/keyrings/kubernetes-archive-keyring.gpg
    echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
    sudo apt-get update
    sudo apt-get install -y kubectl

    # --- Install kind ---
    curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.21.0/kind-linux-amd64
    chmod +x ./kind
    sudo mv ./kind /usr/local/bin/kind

    # --- Install Helm ---
    curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash

    echo "Provisioning complete!"
  SHELL
end
