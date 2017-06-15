# dockerphp5.6
docker phpenv
use docker-compose
contain: nginx php5.6 mysql redis memcached elasticsearch rabbitmq mongo


first: install docker , eg: in centos -- yum install -y docker


and then , install docker-compose


I suggest to use this way:

  yum update -y
  
  yum install epel-release -y 
  
  yum install python-pip -y
  
  pip install docker-compose

at last , docker-compose up

Tips:

  the file 'Dockerfile.bak' in fpm is config of php7.0
  
  when use php7.0 , don't forget to modify the supervisord.conf 
  
  mysql root password setting is not work , but you can use usename:root password:root to connect it
