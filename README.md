# Vagrant IAC (infrastructure as code) #

## purpose ##

Deploy a web app through a vagrant file,

## the bash script presented below: ##

config.vm.provision "shell", inline: <<-SHELL
    yum install httpd wget unzip vim -y
    systemctl start httpd
    systemctl enabled httpd
    mkdir -p /tmp/finance
    cd /tmp/finance
    wget https://www.tooplate.com/zip-templates/2135_mini_finance.zip
    unzip -o 2135_mini_finance.zip
    cp -r 2135_mini_finance/* /var/www/html/
    systemctl stop firewalld
    systemctl disable firewalld
    systemctl restart httpd
    cd /tmp/
    rm -rf /tmp/finance
  SHELL

## Special thanks to https://www.tooplate.com/ for allowing of the use of a free HTML templates ##

