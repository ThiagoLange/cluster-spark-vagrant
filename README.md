
# Cluster Spark 

Vagrantfile para criar um Cluster Spark com um Manager e 2 workers para estudos com  o Vagrant.


## Passo a Passo

[Repositório](https://github.com/ThiagoLange/cluster-spark-vagrant.git)

### 1. Instale o Virtualbox - <https://www.virtualbox.org/wiki/Downloads> disponível para MacOs, Windows e Linux

### 2. Instale o Vagrant - <https://www.vagrantup.com/> disponível para MacOs, Windows e Linux.

### 3. Após a instalação do Virtualbox e Vagrant, instale o plugin vagrant-vbguest caso esteja utilizando windows
```vagrant plugin install vagrant-vbguest --plugin-version 0.21```

### 4. Faça o download do arquivo Vagrantfile.

### 5. Salve ele em um diretório de sua preferência.

### 6. Acesse esse diretório pelo terminal.

### 7. Para iniciar o cluster digite 
```vagrant up```

### 8. Espere finalizar a criação das máquinas virtuais.

### 9. Acesse o manager
```vagrant ssh spark-manager```

### 10. Acessar cluster pelo terminal 
```pyspark --master spark://192.168.56.10:7077```

### 11. Acessando a interfáce gráfica com as informações do cluster digite no seu navegador 
```192.168.56.10:8080```

### Após uso, se quiser parar o cluster
```vagrant halt```

### Caso queira destruir o cluster 
```vagrant destroy```

###### OBS: Esse arquivo pode ser configurado conforme sua necessidade alterando a quantidade de memória e cpu no arquivo conforme você necessita.Também pode ser alterado os IP's
