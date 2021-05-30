#NCNU_INTERVIEW THE SECOND QUESTION

# PART_1: 前製作業--所需套件
#        1. Docker ＆ Docker-compose 安裝
#           Docker 版本:20.10.6 
#           Docker-compose 版本:1.25.4
#        2. MariaDB 安裝 
#           MariaDB 版本:10.5.10 for Ubuntu 18.04 LTS
#           
#           $sudo apt update
#           $sudo apt install mariadb-server
#           $sudo mysql_secure_installation(還沒裝）
#        3. DB GUI 安裝
#           (此處安裝 MySQL Workbench)
#           MySQL Workbench 版本:6.3.8
#           
#           $sudo apt update && sudo apt upgrade
#           $sudo apt install mysql-workbench



# PART_2: 利用docker-compose安裝MariaDB
#         Step_1:建置相關目錄及檔案
#                01.在家目錄下建立目錄:interview-mariadb
#                                 $mkdir interview-mariadb
#                02.在interview-mariadb目錄下建立目錄 dump 及 data
#                  (PATH: ~/interview-mariadb/dump)
#                                  021.$mkdir dump
#                                  022.$mkdir data (存放Database:nantou/Table:puli資料 passwd:12345678)
#                03.在dump目錄下建立檔案 00_init.sql 01_backup.sql 
#                                   $nano 00_init.sql
#                                   $nano 01_backup.sql
#                04.在interview-mariadb目錄下建立檔案 docker-compose.yml (內容於上傳檔案:docker-compose.yml)
#         Step_2:先檢視docker裡是否有運行的container,若有,先停止及清除docker原先資料
#                01. $docker ps -a (docker-compose ps -a/without "CONTAINER ID")
#                02. $docker stop CONTAINER ID (or CONTAINER Name: mariadb02)
#                    ($sudo systemctl stop docker
#                     $sudo systemctl stop docker.socket
#                     $sudo systemctl rm -rf /var/lib/docker
#                     $sudo systemctl start docker
#                     $docker ps -a (check again)
#                     $sudo systemctl status mariadb
#                     $sudo systemctl stop mariadb
#                     $sudo systemctl start mariadb /此法較暴力)
#         Step_3:切換到要運行的目錄下（即docker-compose.yml所在處）
#                01. $docker-compose build（出現mariadb uses an image, skipping)
#                02. $docker-compose up -d
#                03. $docker-compose ps -a (檢視container:mariadb02是否有運行)
#         Step_4:在docker container:mariadb02上執行 MariaDB
#                01. $docker exec -it mariadb02 mysql -u root -p12345678
#         Step_5:在docker container mariadb02 的 MariaDB 建立Database:nantou及Table:puli
#                01. MariaDB[none]> CREATE DATABASE nantou;
#                02. MariaDB[none]> USE nantou;
#                03. MariaDB[none]> CREATE TABLE puli(id integer auto_increment primary key, Name char(30), Hobbies char(50) Tel char(20));
#                04. MariaDB[none]> insert into puli(Name, Hobbies, Tel) values('Wonder Wang', 'Travelling and Sleep', 'Top Secret');
#                05. MariaDB[none]> SELECT*FROM puli; (圖檔 mariadb08.png)
#                06. MariaDB[none]>\q
#         Step_6 使用MySQL Workbench 連線且port設成3316 (圖檔 mariadb03~07.png)
#         Step_7 結束docker
#                $docker stop mariadb02
#                $docker rm mariadb02
#                $docker ps -a           
#

#
#
#
#
#
#
#
#

#

#
#
#
#

#
#
#
#
#

#

#
#
#

#
#
