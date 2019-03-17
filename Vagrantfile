Vagrant.configure("2") do |config|

  config.vm.box = "bento/centos-7.4"

  # メモリを増やしておく
  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
    v.cpus = 2
  end

  # VM 上で初めから Docker を使えるようにしておく
  config.vm.provision "docker"

  config.vm.provision "shell", inline: <<-SHELL
    sudo curl -L https://github.com/docker/compose/releases/download/1.24.0-rc1/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
    sudo chmod +x /usr/local/bin/docker-compose
  SHELL

  # ホスト側にポートフォワーディングして Web の画面を見れたりデータベースアクセスできたりするようにしておく
  config.vm.network "private_network", ip: "192.168.33.11"

  # ホスト側の docker-compose.yml などのファイルを VM 内で参照するため共有しておく
  config.vm.synced_folder "C:/work/vodSearch", "/home/vagrant/vodSearch"

end
