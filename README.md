# daniel-info
##Instalação Servidor
​
Ao Criar o servidor EC2 deve atualizar e instalar os seguintes pacotes:
yum update
yum install httpd24 (apache) fazer o service httpd start e confirmar se o apache esta executando no browser com o endereço do servidor.
yum install php70 (php) testar uma pagina com codigo em php e salvar index.php na pasta /var/www/html e testar o php

##Instalação do RDS Mysql
​
Criar um RDS Mysql versão 5.7 com acesso apenas a rede interna amazon na porta 3306, usuario e senha do banco.

##Configurar o acesso Mysql e criar Database para o Worpress
​
No servidor apache instalar o mysql
yum install mysql
Conectar no servidor RDS através do comando: mysql -h database-1.cndqlf2jwce3.us-east-2.rds.amazonaws.com -P 3306 -u admin -p
Criar um database: create databse caseinfo;

##Instalar o Worpress e configurar o Mysql RDS
​
wget https://wordpress.org/latest.tar.gz (Instalar a última versão)
tar -xzf latest.tar.gz (desconpactar o arquivo)
cd wordpress/ (acessar a pasta Wordpress)
cp wp-config-sample.php wp-config.php (copiar o arquivo de configuração)
vim wp-config.php (editar o arquivo de configuração com as seguintes informações:

  Encontrar no arquivo e editar:
define('DB_NAME', 'nome da base');
define('DB_USER', 'usuario');
define('DB_PASSWORD', 'senha');
define('DB_HOST', 'endpoint do rds mysql');

https://api.wordpress.org/secret-key/1.1/salt/ (acessar este endereço e copiar as linhas para cookies que o WordPress e substituir no arquivo )
  Encontrar no arquivo, deletar e colar as linhas:
  
define('AUTH_KEY',         ' #U$$+[RXN8:b^-L 0(WU_+ c+WFkI~c]o]-bHw+)/Aj[wTwSiZ<Qb[mghEXcRh-');
define('SECURE_AUTH_KEY',  'Zsz._P=l/|y.Lq)XjlkwS1y5NJ76E6EJ.AV0pCKZZB,*~*r ?6OP$eJT@;+(ndLg');
define('LOGGED_IN_KEY',    'ju}qwre3V*+8f_zOWf?{LlGsQ]Ye@2Jh^,8x>)Y |;(^[Iw]Pi+LG#A4R?7N`YB3');
define('NONCE_KEY',        'P(g62HeZxEes|LnI^i=H,[XwK9I&[2s|:?0N}VJM%?;v2v]v+;+^9eXUahg@::Cj');
define('AUTH_SALT',        'C$DpB4Hj[JK:?{ql`sRVa:{:7yShy(9A@5wg+`JJVb1fk%_-Bx*M4(qc[Qg%JT!h');
define('SECURE_AUTH_SALT', 'd!uRu#}+q#{f$Z?Z9uFPG.${+S{n~1M&%@~gL>U>NV<zpD-@2-Es7Q1O-bp28EKv');
define('LOGGED_IN_SALT',   ';j{00P*owZf)kVD+FVLn-~ >.|Y%Ug4#I^*LVd9QeZ^&XmK|e(76miC+&W&+^0P/');
define('NONCE_SALT',       '-97r*V/cgxLmp?Zy4zUU4r99QQ_rGs2LTd%P;|_e1tS)8_B/,.6[=UK<J_y9?JWG');



​
 - O projeto dever ser configurado na [AWS](https://aws.amazon.com/free/), crie uma conta Free.
 - A máquina configurada deverar ter às portas 80, 443 e 22 abertas.
 - Uso de Shell Script **Linux**.
 - [Docker](https://www.docker.com/) 
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
