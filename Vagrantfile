Vagrant.configure("2") do |config|

  config.vm.box = "bento/centos-7.4"

  # vagrantのリソースを設定
  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
    v.cpus = 2
  end

# docker、docker-composeのインストール
  config.vm.provision "docker"
  config.vm.provision "shell", inline: <<-SHELL
    sudo curl -L https://github.com/docker/compose/releases/download/1.24.0-rc1/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
    sudo chmod +x /usr/local/bin/docker-compose
  SHELL

  # ローカルからアクセスするためのIPを設定
  config.vm.network "private_network", ip: "192.168.33.11"

  # ローカル・ゲスト間の共有フォルダを設定
  config.vm.synced_folder "C:/work/vodSearch", "/home/vagrant/vodSearch"

end
