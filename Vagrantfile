# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  
  config.vm.define "spark-manager" do |manager|
    manager.vm.box = "ubuntu/focal64"
    manager.vm.hostname = "spark-manager"
    manager.vm.network "private_network", ip: "192.168.56.10"
    
    manager.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
      vb.cpus = 2
    end
    
    manager.vm.provision "shell", inline: <<-SHELL
      # Atualizar pacotes e instalar o Java
      apt-get update
      apt-get install -y default-jdk
      
      # Baixar o Apache Spark
      wget -q https://dlcdn.apache.org/spark/spark-3.3.2/spark-3.3.2-bin-hadoop3.tgz
      
      # Descompactar o Spark
      tar -xzf spark-3.3.2-bin-hadoop3.tgz

      # mover para diretório /opt/
      sudo mv spark-3.3.2-bin-hadoop3 /opt/spark

      # Configurar variáveis de ambiente
      echo 'export SPARK_HOME=/opt/spark' >> /home/vagrant/.bashrc
      echo 'export PATH=$PATH:$SPARK_HOME/bin' >> /home/vagrant/.bashrc
      source .bashrc

      # Configurar Spark Master
      sudo cp /opt/spark/conf/spark-env.sh.template /opt/spark/spark-env.sh
      echo 'SPARK_MASTER_HOST=192.168.56.10' >> /opt/spark/conf/spark-env.sh 

      # iniciar spark master
      sudo /opt/spark/sbin/start-master.sh

      # iniciar spark slaves
      # sudo /opt/spark/sbin/start-worker.sh spark://192.168.56.10:7077
    SHELL
  end
  
  config.vm.define "spark-worker1" do |worker1|
    worker1.vm.box = "ubuntu/focal64"
    worker1.vm.hostname = "spark-worker1"
    worker1.vm.network "private_network", ip: "192.168.56.11"
    
    worker1.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
      vb.cpus = 2
    end
    
    worker1.vm.provision "shell", inline: <<-SHELL
      # Atualizar pacotes e instalar o Java
      apt-get update
      apt-get install -y default-jdk
      
      # Baixar o Apache Spark
      wget -q https://dlcdn.apache.org/spark/spark-3.3.2/spark-3.3.2-bin-hadoop3.tgz
      
      # Descompactar o Spark
      tar -xzf spark-3.3.2-bin-hadoop3.tgz

      # mover para diretório /opt/
      sudo mv spark-3.3.2-bin-hadoop3 /opt/spark
      
      # Configurar variáveis de ambiente
      echo 'export SPARK_HOME=/opt/spark' >> /home/vagrant/.bashrc
      echo 'export PATH=$PATH:$SPARK_HOME/bin' >> /home/vagrant/.bashrc
      source .bashrc

      # Configurar Spark Master
      sudo cp /opt/spark/conf/spark-env.sh.template /opt/spark/spark-env.sh
      echo 'SPARK_MASTER_HOST=192.168.56.10' >> /opt/spark/conf/spark-env.sh

      # iniciar spark slaves
      sudo /opt/spark/sbin/start-worker.sh spark://192.168.56.10:7077
    SHELL
  end
  
  config.vm.define "spark-worker2" do |worker2|
    worker2.vm.box = "ubuntu/focal64"
    worker2.vm.hostname = "spark-worker2"
    worker2.vm.network "private_network", ip: "192.168.56.12"
    
    worker2.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
      vb.cpus = 2
    end
    
    worker2.vm.provision "shell", inline: <<-SHELL
      # Atualizar pacotes e instalar o Java
      apt-get update
      apt-get install -y default-jdk
      
      # Baixar o Apache Spark
      wget -q https://dlcdn.apache.org/spark/spark-3.3.2/spark-3.3.2-bin-hadoop3.tgz

      # Descompactar o Spark
      tar -xzf spark-3.3.2-bin-hadoop3.tgz

      # mover para diretório /opt/
      sudo mv spark-3.3.2-bin-hadoop3 /opt/spark
      
      # Configurar variáveis de ambiente
      echo 'export SPARK_HOME=/opt/spark' >> /home/vagrant/.bashrc
      echo 'export PATH=$PATH:$SPARK_HOME/bin' >> /home/vagrant/.bashrc
      source .bashrc

      # Configurar Spark Master
      sudo cp /opt/spark/conf/spark-env.sh.template /opt/spark/spark-env.sh
      echo 'SPARK_MASTER_HOST=192.168.56.10' >> /opt/spark/conf/spark-env.sh

      # iniciar spark slaves
      sudo /opt/spark/sbin/start-worker.sh spark://192.168.56.10:7077
    SHELL
  end
end
