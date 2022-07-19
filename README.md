# Task
Part 1:
	1-"pvcreate /dev/sdb
	   vgcreate -s 16M  LVM /dev/sdb
	   lvcreate -n lvm1 LVM  -l 50 /dev/sdb
	   mkfs.ext4 /dev/LVM/lvm1
	   mkdir -vp /mnt/data
	   mount /dev/LVM/lvm1 /mnt/data"



Part 2:
	1- "useradd -u 601 -s /sbin/nologin -p redhat user1"
	2- "usermod -a -G TrainingGroup user1"
	3- "useradd user2
	    useradd user3
	    groupadd -p redhat admingroup
	    usermod -a -G root user3
	    usermod -g 0 -o -u 1002 user3"
part 3:
	1-"ssh-keygen #on the remote 
	   ssh-copy-id centos@172.20.48.20
	   ssh centos@172.20.48.20"


Part 4:
	1- "cp /etc/fstab /var/tmp
	    setfacl -m u:user1:rwx /var/tmp/fstab
	    setfacl -m u:user2:--- /var/tmp/fstab"

Part 5:
	1-"vi /etc/selinux/config"
	  and put SELINUX line to enforcing
Part 6:
	1-"(c=0; while [ $c -lt 600 ]; do c=`expr $c + 1`;  sleep 1; done) &
	   jobs   ### it says running 
           kill <pid>  ### in my case it was 18389 
	   jobs ### it now says Terminated"

Part 7:
	1-"sudo yum -y install tmux"
	2-"sudo yum update httpd
	   sudo yum install httpd"
	3-"sudo systemctl start httpd
	   sudo systemctl enable httpd
	   sudo systemctl status httpd
	   sudo yum install createrepo yum-utils
	   mkdir /var/www/html/zabbix	
	   sudo createrepo /var/www/html/zabbix
	   sudo wget https://repo.zabbix.com/zabbix/4.4/rhel/7/x86_64/zabbix-agent-4.4.0-1.el7.x86_64.rpm -P /var/www/html/zabbix --no-check-certificate
	   vi /etc/yum.repos.d/zabbix.repo" => {  [zabixx] 

						 name=zabbix

						 baseurl=file:///var/www/html/zabbix

						 enabled=1

						 gpgcheck=0  }
	   "yum --enablerepo=zabbixx install zabbix-agent-4.4.0-1.el7.x86_64" => Worked perfectly 👌 
	      
	   




Part 8:
	1-" firewall-cmd --zone=public --add-port=443/udp --permanent ## <- (2-)
	    firewall-cmd --zone=public --add-port=80/tcp --permanent  ## <- (2-)
	    firewall-cmd --reload"
	3-"firewall-cmd --direct --add-rule ipv4 filter INPUT 1 -m tcp --source 192.168.1.100 -p tcp --dport 22 -j REJECT ####ip is for example
	   firewall-cmd --reload" 


Part 9:
	1-Create a script=> "vi myscr.sh" =>{ #!/bin/bash
					      date
				              echo "-"
					      whoami }

	  "chmod +x myscr.sh
	   crontab -e" => { 30 1 * * * /home/centos/myscr.sh >> /tmp/output }

Part 10:
	"yum install --downloadonly mariadb-server
	 firewall-cmd --zone=public --add-service=mysql --permanent
	 iptables-save | grep 3306
	 service mariadb start
	 /usr/bin/mysql_secure_installation
	 mysql -u root -p
	 use mysql" 
create table rhce1(
    id int auto_increment
    student_firstname varchar(50) not null,
    student_lastname varchar(50) not null,
    program varchar(50) not null,
    graduation_year varchar(50) not null,
    primary key(id)
);

insert into   rhce1 (  id,  student_firstname,    student_lastname,     program,     graduation_year   ) values   (001, 'allen', 'brown', 'mechanical', '2017');
insert into   rhce1 (  id,  student_firstname,    student_lastname,     program,     graduation_year   ) values   (002, 'David', 'brown', 'mechanical', '2017');
insert into   rhce1 (  id,  student_firstname,    student_lastname,     program,     graduation_year   ) values   (003, 'Mary', 'green', 'mechanical', '2018');
insert into   rhce1 (  id,  student_firstname,    student_lastname,     program,     graduation_year   ) values   (004, 'Dennis', 'green', 'electrical', '2018');
insert into   rhce1 (  id,  student_firstname,    student_lastname,     program,     graduation_year   ) values   (005, 'Joseph', 'black', 'electrical', '2018');
insert into   rhce1 (  id,  student_firstname,    student_lastname,     program,     graduation_year   ) values   (006, 'Dennis', 'black', 'electrical', '2020');
insert into   rhce1 (  id,  student_firstname,    student_lastname,     program,     graduation_year   ) values   (007, 'Ritchie', 'salt', 'computer science', '2020');
insert into   rhce1 (  id,  student_firstname,    student_lastname,     program,     graduation_year   ) values   (008, 'Robert', 'salt', 'computer science', '2020');
insert into   rhce1 (  id,  student_firstname,    student_lastname,     program,     graduation_year   ) values   (009, 'David', 'suzuki', 'computer science', '2020');
insert into   rhce1 (  id,  student_firstname,    student_lastname,     program,     graduation_year   ) values   (010, 'Mary', 'Chen', 'computer science', '2020');

MariaDB [mysql]> SELECT * FROM rhce1;
+----+-------------------+------------------+------------------+-----------------+
| id | student_firstname | student_lastname | program          | graduation_year |
+----+-------------------+------------------+------------------+-----------------+
|  1 | allen             | brown            | mechanical       |            2017 |
|  2 | David             | brown            | mechanical       |            2017 |
|  3 | Mary              | green            | mechanical       |            2018 |
|  4 | Dennis            | green            | electrical       |            2018 |
|  5 | Joseph            | black            | electrical       |            2018 |
|  6 | Dennis            | black            | electrical       |            2020 |
|  7 | Ritchie           | salt             | computer science |            2020 |
|  8 | Robert            | salt             | computer science |            2020 |
|  9 | David             | suzuki           | computer science |            2020 |
| 10 | Mary              | Chen             | computer science |            2020 |
+----+-------------------+------------------+------------------+-----------------+
