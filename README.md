### Backend Server Configuration,

**Installed Java,**

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo apt install openjdk-19-jre-headless (Tomcat 11 requires latest version of Java)`

`anup@ubuntu-22041-100-REALMREGAL:~$ java -version`

`anup@ubuntu-22041-100-REALMREGAL:~$ update-alternatives --config java`

<br>

### Download Tomcat, https://dlcdn.apache.org/tomcat/

`anup@ubuntu-22041-100-REALMREGAL:~$ wget https://dlcdn.apache.org/tomcat/tomcat-11/v11.0.0-M4/bin/apache-tomcat-11.0.0-M4.tar.gz`

`anup@ubuntu-22041-100-REALMREGAL:~$ ls -ltr`

<br>

### Setup backend-7070,

`anup@ubuntu-22041-100-REALMREGAL:~$ tar -xvzf apache-tomcat-11.0.0-M4.tar.gz `

`anup@ubuntu-22041-100-REALMREGAL:~$ mv apache-tomcat-11.0.0-M4 apache-tomcat-11.0.0-M4-7070`

`anup@ubuntu-22041-100-REALMREGAL:~$ ln -sf apache-tomcat-11.0.0-M4-7070 backend-7070`

`anup@ubuntu-22041-100-REALMREGAL:~$ cd backend-7070`

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-7070$ nano conf/server.xml `

    <Server port="7005" shutdown="SHUTDOWN">
    
        <Connector port="7070" protocol="HTTP/1.1"
                   connectionTimeout="20000"
                   redirectPort="7443" />

<br>

    <!-- Define an AJP 1.3 Connector on port 7009 -->
    
    <Connector protocol="AJP/1.3"
               address="192.168.56.100"
               port="7009"
               redirectPort="7443"
               secretRequired="false" />

<br>

    <Engine name="Catalina" defaultHost="localhost" jvmRoute="worker1">

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-7070$ sudo nano conf/tomcat-users.xml`

    <tomcat-users xmlns="http://tomcat.apache.org/xml"
       <role rolename="admin-gui"/>
       <role rolename="manager-gui"/>
       <user username="admin" password="0tm7s^6IeVs5" roles="admin-gui,manager-gui"/>
    </tomcat-users

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-7070$ sudo nano webapps/manager/META-INF/context.xml`

    <!--
      <Valve className="org.apache.catalina.valves.RemoteAddrValve"
             allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
    -->

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-7070$ sudo nano webapps/host-manager/META-INF/context.xml`

    <!--
      <Valve className="org.apache.catalina.valves.RemoteAddrValve"
             allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
    -->

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-7070$ ./bin/shutdown.sh`

`anup@ubuntu-22041-100-REALMREGAL:~/backend-7070$ ./bin/startup.sh`

<br>

### Setup backend-8080,

`anup@ubuntu-22041-100-REALMREGAL:~$ tar -xvzf apache-tomcat-11.0.0-M4.tar.gz `

`anup@ubuntu-22041-100-REALMREGAL:~$ mv apache-tomcat-11.0.0-M4 apache-tomcat-11.0.0-M4-7070`

`anup@ubuntu-22041-100-REALMREGAL:~$ ln -sf apache-tomcat-11.0.0-M4-7070 backend-7070`

`anup@ubuntu-22041-100-REALMREGAL:~$ cd backend-8080`

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-8080$ nano conf/server.xml `

    <Server port="8005" shutdown="SHUTDOWN">
    
        <Connector port="8080" protocol="HTTP/1.1"
                   connectionTimeout="20000"
                   redirectPort="8443" />

<br>

    <!-- Define an AJP 1.3 Connector on port 8009 -->
    
    <Connector protocol="AJP/1.3"
               address="192.168.56.100"
               port="8009"
               redirectPort="8443"
               secretRequired="false" />

<br>

    <Engine name="Catalina" defaultHost="localhost" jvmRoute="worker2">

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-8080$ sudo nano conf/tomcat-users.xml`

    <tomcat-users xmlns="http://tomcat.apache.org/xml"
       <role rolename="admin-gui"/>
       <role rolename="manager-gui"/>
       <user username="admin" password="0tm7s^6IeVs5" roles="admin-gui,manager-gui"/>
    </tomcat-users

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-8080$ sudo nano webapps/manager/META-INF/context.xml`

    <!--
      <Valve className="org.apache.catalina.valves.RemoteAddrValve"
             allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
    -->

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-8080$ sudo nano webapps/host-manager/META-INF/context.xml`

    <!--
      <Valve className="org.apache.catalina.valves.RemoteAddrValve"
             allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
    -->

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-8080$ ./bin/shutdown.sh`

`anup@ubuntu-22041-100-REALMREGAL:~/backend-8080$ ./bin/startup.sh`

<br>

### Setup backend-9090,

`anup@ubuntu-22041-100-REALMREGAL:~$ tar -xvzf apache-tomcat-11.0.0-M4.tar.gz `

`anup@ubuntu-22041-100-REALMREGAL:~$ mv apache-tomcat-11.0.0-M4 apache-tomcat-11.0.0-M4-7070`

`anup@ubuntu-22041-100-REALMREGAL:~$ ln -sf apache-tomcat-11.0.0-M4-7070 backend-7070`

`anup@ubuntu-22041-100-REALMREGAL:~$ cd backend-9090`

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-9090$ nano conf/server.xml `

    <Server port="9005" shutdown="SHUTDOWN">
    
        <Connector port="9090" protocol="HTTP/1.1"
                   connectionTimeout="20000"
                   redirectPort="9443" />

<br>

    <!-- Define an AJP 1.3 Connector on port 9009 -->
    
    <Connector protocol="AJP/1.3"
               address="192.168.56.100"
               port="9009"
               redirectPort="9443"
               secretRequired="false" />

<br>

    <Engine name="Catalina" defaultHost="localhost" jvmRoute="worker3">

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-9090$ sudo nano conf/tomcat-users.xml`

    <tomcat-users xmlns="http://tomcat.apache.org/xml"
       <role rolename="admin-gui"/>
       <role rolename="manager-gui"/>
       <user username="admin" password="0tm7s^6IeVs5" roles="admin-gui,manager-gui"/>
    </tomcat-users

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-9090$ sudo nano webapps/manager/META-INF/context.xml`

    <!--
      <Valve className="org.apache.catalina.valves.RemoteAddrValve"
             allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
    -->

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-9090$ sudo nano webapps/host-manager/META-INF/context.xml`

    <!--
      <Valve className="org.apache.catalina.valves.RemoteAddrValve"
             allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
    -->

<br>

`anup@ubuntu-22041-100-REALMREGAL:~/backend-9090$ ./bin/shutdown.sh`

`anup@ubuntu-22041-100-REALMREGAL:~/backend-9090$ ./bin/startup.sh`


### Update System and Installing Apache - https://ubuntu.com/tutorials/install-and-configure-apache#1-overview

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo apt update`

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo apt install apache2`

<br>

### Manage services,

`anup@ubuntu-22041-100-REALMREGAL:~$ apache2 -v`

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo systemctl status apache2.service `

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo systemctl enable apache2.service `

<br>

### Adjusting the Firewall,

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo ufw status`

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo ufw enable `

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo ufw app list`

<br>

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo ufw allow 'Apache'`

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo ufw allow 80/tcp`

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo ufw allow 443/tcp`

<br>

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo ufw allow ssh`

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo ufw allow 22/tcp`

<br>

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo ufw status`

<br>

### Checking your Web Server,

http://192.168.56.100/

<br>

### Configuration, On Load Balancer Server, 192.168.56.100:80

`anup@ubuntu-22041-100-REALMREGAL:~$ apachectl configtest`

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo nano /etc/apache2/apache2.conf`

    ServerName 192.168.56.100

`anup@ubuntu-22041-100-REALMREGAL:~$ apachectl configtest`

<br>

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo nano /etc/hosts`

    192.168.56.100       ubuntu-22041-100-REALMREGAL

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo nano /etc/hostname `

    ubuntu-22041-100-REALMREGAL

`anup@ubuntu-22041-100-REALMREGAL:~$ ls -ltr /etc/apache2/sites-available`

`anup@ubuntu-22041-100-REALMREGAL:~$ ls -ltr /etc/apache2/sites-enabled/`

<br>

`anup@ubuntu-22041-100-REALMREGAL:~$ cd /etc/apache2/sites-available/`

`anup@ubuntu-22041-100-REALMREGAL:/etc/apache2/sites-available$ sudo cp 000-default.conf 000-default.conf.backup`

<br>

### Enabling Necessary Apache Modules,

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo a2enmod proxy proxy_http proxy_balancer lbmethod_byrequests`

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo systemctl restart apache2.service `

<br>

### Modifying the Default Configuration to Enable Reverse Proxy,

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo nano /etc/apache2/sites-available/000-default.conf`

    <VirtualHost *:80>
        ProxyPreserveHost On
    
        ProxyPass / http://192.168.56.100:8080/
        ProxyPassReverse / http://192.168.56.100:8080/
    </VirtualHost>


`anup@ubuntu-22041-100-REALMREGAL:~$ apachectl configtest`

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo systemctl restart apache2`

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo systemctl status apache2`

<br>

### Checking your Web Server,

http://192.168.56.100/

<br>

### Load Balancing Across Multiple Backend Servers,

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo nano /etc/apache2/sites-available/000-default.conf`

    <VirtualHost *:80>
    <Proxy balancer://mycluster>
        BalancerMember http://192.168.56.100:7070/
        BalancerMember http://192.168.56.100:8080/
        BalancerMember http://192.168.56.100:9090/
    </Proxy>
    
        ProxyPreserveHost On
    
        ProxyPass / balancer://mycluster/
        ProxyPassReverse / balancer://mycluster/
    </VirtualHost>

`anup@ubuntu-22041-100-REALMREGAL:~$ apachectl configtest`

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo systemctl restart apache2`

`anup@ubuntu-22041-100-REALMREGAL:~$ sudo systemctl status apache2`

<br>
