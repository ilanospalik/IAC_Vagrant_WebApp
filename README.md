# Vagrant IAC (infrastructure as code) #

## purpose ##

Deploy a web app through a vagrant file

## the bash script presented below: ##

config.vm.provision "shell", inline: <<-SHELL
1.    yum install httpd wget unzip vim -y
2.    systemctl start httpd
3.    systemctl enabled httpd
4.    mkdir -p /tmp/finance
5.    cd /tmp/finance
6.    wget https://www.tooplate.com/zip-templates/2135_mini_finance.zip
7.    unzip -o 2135_mini_finance.zip
8.    cp -r 2135_mini_finance/* /var/www/html/
9.    systemctl stop firewalld
10.   systemctl disable firewalld
11.   systemctl restart httpd
12.   cd /tmp/
13.   rm -rf /tmp/finance
  SHELL

## Special thanks to https://www.tooplate.com/ for allowing of the use of a free HTML templates ##

