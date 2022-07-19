# Terraform_HA_WebServer
This code builds a high availability cluster on AWS using Terraform

### In the file user_data.sh we configure the server:
* we install the web server.
* generate a web page for display
````
#!/bin/bash
yum -y update
yum -y install httpd


myip='curl http://169.254.169.254/latest/meta-data/local-ipv4'

cat <<EOF > /var/www/html/index.html
<html>
<body bgcolor="black">
<h2><font color="gold"> Build by Terraform</font></h2><br><p>
<font color="green">Server PrivateIP: <font color="aqua">$myip<bp><br>
<title>Terraform</title><br>
<font color="magenta">
<b>Version1.0</b>
</body>
</html>
EOF

sudo service httpd start
chkconfig httpd on
````

### In the file main.tf we describe the infrastructure in AWS:
* 
