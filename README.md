# daniel-info

### Instalação do Servidor!
​
  - Ao Criar o servidor EC2 deve atualizar e instalar os seguintes pacotes:
     - sudo su (entrar com superusuário)
     - yum update (atualizar pacotes).
     - yum install httpd24 (apache) fazer o service httpd start e confirmar se o apache esta executando no browser com o endereço do servidor AWS.
     - yum install php70 (php) testar uma pagina com codigo em php e salvar index.php na pasta /var/www/html e testar o php.
 
 ### Instalação do RDS Mysql 5.7! 
​
  - Criar um RDS Mysql versão 5.7 com acesso apenas a rede interna amazon na porta 3306, usuario e senha do banco.
     
  ### Configurar o acesso Mysql e criar Databade para o Wordpress!  
​
  - No servidor apache instalar o mysql:
     - yum install mysql.
     - Conectar no servidor RDS através do comando: mysql -h database-1.cndqlf2jwce3.us-east-2.rds.amazonaws.com -P 3306 -u admin -p.
     - Criar um database: create databse caseinfo.
     
  ### Instalar o Wordpress e configurar o Mysql RDS!  
​
  - wget https://wordpress.org/latest.tar.gz (Instalar a última versão):
  - tar -xzf latest.tar.gz (desconpactar o arquivo).
  - cd wordpress/ (acessar a pasta Wordpress).
  - cp wp-config-sample.php wp-config.php (copiar o arquivo de configuração).
  - vim wp-config.php (editar o arquivo de configuração com as seguintes informações:
  
     - Encontrar no arquivo e editar:
     
           -define('DB_NAME', 'nome da base');
           -define('DB_USER', 'usuario');
           -define('DB_PASSWORD', 'senha');
           -define('DB_HOST', 'endpoint do rds mysql');
        
     - https ://api.wordpress.org/secret-key/1.1/salt/ (acessar este endereço e copiar as linhas para cookies que o WordPress e substituir no arquivo )
     - Encontrar no arquivo, deletar e colar todas as linhas do site:
    
          -define('AUTH_KEY',         'XyOG`meM9KCY%s%SJhsy171hhMfw4MnW#VMne3y-EE 2r.1l0tQTAZDAL`OwwjCH');
          -define('SECURE_AUTH_KEY',  '$8gTHj|AAsy4LV|?^o<i<E|X)3ulta _{5SOp^WiT_2S4Tfav=j#OGV*ik4_:(Ba');
          -define('LOGGED_IN_KEY',    '2ybXyg%+TkaVMUj5/=jmxYRq1E,W!CWt^Hpxj?#qq0-1|j!#CmKM5+UI-?Ec7 Q/');
          -define('NONCE_KEY',        'k?0KIKi?A^^ve=.-v5egYd!czzvOxbd,%$rs%,&Ar8WtU<oQ+LP.B}c4g0b7b-j:');
     
  - Salvar o arquivo
  - yum install php70-mysql (php usar o banco mysql)
  - mv wordpress/* . (mover todos os arquivos da pasta para /var/www/html)
  - rm -rf wordpress (deletar a pasta do wordpress vazia)
  - chown -R apache:apache (alterar usuário dos arquivos da pasta /var/www/html)
  - acessar o endereço so servidor e concluir a instalação do Wordpress informando os dados de acesso usuario e senha do Banco  
  
### Instalar o Wordpress e configurar o Mysql RDS!

​

  - O projeto dever ser configurado na [AWS](https://aws.amazon.com/free/), crie uma conta Free.
  - A máquina configurada deverar ter às portas 80, 443 e 22 abertas.
  - Uso de Shell Script **Linux**.
  - [Docker](https://www.docker.com/) 

### Arquitertura!
​
 - [Nginx](https://www.nginx.com/) configurado como proxy para o Apache.
 - [Apache](https://www.apache.org/) servidor para o WordPress.
 - [PHP](https://php.net/) a última versão.
 - [MySql](https://www.mysql.com/) Versão mínima requirida 5.7.
 - [WordPress](https://wordpress.org) última versão configurada no servidor Apache.

 **Modelo conceitual**
​

  - [Nginx](https://www.nginx.com/) configurado como proxy para o Apache.
  - [Apache](https://www.apache.org/) servidor para o WordPress.
  - [PHP](https://php.net/) a última versão.
  - [MySql](https://www.mysql.com/) Versão mínima requirida 5.7.
  - [WordPress](https://wordpress.org) última versão configurada no servidor Apache.
  
  **Modelo conceitual**

[![N|Solid](https://apiki.com/wp-content/uploads/2019/05/Screenshot_20190515_174205.png)](https://docs.nginx.com/nginx/admin-guide/web-server/reverse-proxy/)
​

---
​

### Se liga!
​

Você também pode usar como **Diferencial**:

 - [Docker Compose](https://docs.docker.com/compose/).
 - [Kubernetes](https://kubernetes.io/).
 - [Ansible](https://www.ansible.com/).
 - [RDS AWS](https://aws.amazon.com/pt/rds/).
 - Outras tecnologias para somar no projeto. 
​
  
  - [Docker Compose](https://docs.docker.com/compose/).
  - [Kubernetes](https://kubernetes.io/).
  - [Ansible](https://www.ansible.com/).
  - [RDS AWS](https://aws.amazon.com/pt/rds/).
  - Outras tecnologias para somar no projeto.  

---
​

### Entrega
​

1. Efetue o fork deste repositório e crie um branch com o seu nome e sobrenome. (exemplo: fulano-dasilva)
2. Após finalizar o desafio, crie um Pull Request.
3. Aguarde algum contribuidor realizar o code review.
4. Deverá conter a documentação para instalação e configuração README.md.
5. Enviar para o email wphost@apiki.com os dados de acesso SSH com permissão root, da máquina configurada na AWS.
​

---
​

### Validação
​

* Será executado os precessos de instalação e configuração de acordo com a orientação da documentação em um servidor interno da Apiki.
* Será avaliado o processo de automação para criação do ambiente em cloud, tempo de execução e a configuração no server na AWS com os dados fornecidos pelo candidato.
* Deverar constar pelo menos 2 containers.
