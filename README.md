Eddie Chernet CNE370
# Project Title
Real World Project: Database Shard GitHub.

## Getting Started
The project shows how to architecture backend servers and shard the Data with two servers using Maxscale server and shows the client accessing one server but its's accessing two master MariaDB servers connecting with maxscale.

## Requirements
The requirements are virtual machine running with OS ubuntu 22.04.1, and install docker, docker-compose.

How to install docker
sudo apt update
sudo apt install
apt-transport-https ca-certificates curl software-properties-common curl -fsSL https://download.docker.com/linux/ubuntu/gpg |
sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
sudo apt update sudo apt install docker-ce

To see the Docker status with command line. 
sudo systemctl run docker
sudo systenctl enable docker 
sudo systemctl status docker.

Installation Docker Compose: 
sudo apt install docker-compose.

Install client access to MariaDB sudo apt install MariaDB-client. then clone maxscale-docker repository from zohan GitHub. git clone https://github.com/Zohan/maxscale-docker.git use the correct directory to run the docker-compose up  "maxscale-docker/maxscale" docker-compose up -d check all servers states then use the command. root@Maxscale:/home/eddie/maxscale/maxscale-docker/maxscale# docker-compose up -d

Image

<img width="426" alt="Screenshot 2023-03-20 231129" src="https://user-images.githubusercontent.com/103545139/227631854-2f5a4d76-91fc-4664-9638-1feba830a535.png">



	
once it's set up use the command to comform the status of the server root@Maxscale:/home/eddie/maxscale/maxscale-docker/maxscale# docker ps -a

Image
<img width="922" alt="Screenshot 2023-03-24 233257 pngnew" src="https://user-images.githubusercontent.com/103545139/227701127-1d66a4be-7cb2-4527-82fc-2fa75fc6982c.png">

	


The following command tests the servers are running and connecting to ports. root@Maxscale:/home/eddie/maxscale/maxscale-docker/maxscale# docker-compose exec maxscale maxctrl list servers

Image
<img width="539" alt="Screenshot 2023-03-24 233643 png1" src="https://user-images.githubusercontent.com/103545139/227701312-8c529129-dad6-4979-860f-58b95a6582af.png">

	


	
Use this command if master is down and how to master2 become master1. docker-compose stop master.

Image
<img width="545" alt="Screenshot 2023-03-24 234019 png2" src="https://user-images.githubusercontent.com/103545139/227701549-2b42dbb0-ede6-44df-95d1-fe187b959e6e.png">
	
	
This command is to create client to access the databases and it's possible to acceses data from mysql console.
	mariadb -umaxuser -pmaxpwd -h 127.0.0.1 -P 4000

Image
<img width="534" alt="Screenshot 2023-03-20 232549" src="https://user-images.githubusercontent.com/103545139/227632232-85c1a01f-1922-479f-91a6-0496d6077b42.png">
	


	
This command is to show the databases in our server
show databases;

Image
<img width="539" alt="Screenshot 2023-03-20 233014" src="https://user-images.githubusercontent.com/103545139/227632374-37aee986-349a-402e-bfcc-ec30cd16d731.png">
	


	
use a command is to access both servers from my maxscale server


Image
<img width="539" alt="Screenshot 2023-03-20 233014" src="https://user-images.githubusercontent.com/103545139/227632438-5def785f-282a-43bf-99c5-fcedc9c5952e.png">
	

	
## Using python to access remotely our maxscale server

# Running python

## This is the output when I run shard project1.py from my pycharm.

## The last 10 rows of zipcodes_one are:

(40843, 'STANDARD', 'HOLMES MILL', 'KY', 'PRIMARY', '36.86', '-83', 'NA-US-KY-HOLMES MILL', 'FALSE', '', '', '') (41425, 'STANDARD', 'EZEL', 'KY', 'PRIMARY', '37.89', '-83.44', 'NA-US-KY-EZEL', 'FALSE', '390', '801', '10204009') (40118, 'STANDARD', 'FAIRDALE', 'KY', 'PRIMARY', '38.11', '-85.75', 'NA-US-KY-FAIRDALE', 'FALSE', '4398', '7635', '122449930') (40020, 'PO BOX', 'FAIRFIELD', 'KY', 'PRIMARY', '37.93', '-85.38', 'NA-US-KY-FAIRFIELD', 'FALSE', '', '', '') (42221, 'PO BOX', 'FAIRVIEW', 'KY', 'PRIMARY', '36.84', '-87.31', 'NA-US-KY-FAIRVIEW', 'FALSE', '', '', '') (41426, 'PO BOX', 'FALCON', 'KY', 'PRIMARY', '37.78', '-83', 'NA-US-KY-FALCON', 'FALSE', '', '', '') (40932, 'PO BOX', 'FALL ROCK', 'KY', 'PRIMARY', '37.22', '-83.78', 'NA-US-KY-FALL ROCK', 'FALSE', '', '', '') (40119, 'STANDARD', 'FALLS OF ROUGH', 'KY', 'PRIMARY', '37.6', '-86.55', 'NA-US-KY-FALLS OF ROUGH', 'FALSE', '760', '1468', '20771670') (42039, 'STANDARD', 'FANCY FARM', 'KY', 'PRIMARY', '36.75', '-88.79', 'NA-US-KY-FANCY FARM', 'FALSE', '696', '1317', '20643485') (40319, 'PO BOX', 'FARMERS', 'KY', 'PRIMARY', '38.14', '-83.54', 'NA-US-KY-FARMERS', 'FALSE', '', '', '')

	Image python
	<img width="920" alt="py" src="https://user-images.githubusercontent.com/103545139/227703017-e5965e60-70a4-490e-92e8-8aeaf99e1510.png">

	

	
## The first 10 rows of zipcodes_two are:

(42040, 'STANDARD', 'FARMINGTON', 'KY', 'PRIMARY', '36.67', '-88.53', 'NA-US-KY-FARMINGTON', 'FALSE', '465', '896', '11562973') (41524, 'STANDARD', 'FEDSCREEK', 'KY', 'PRIMARY', '37.4', '-82.24', 'NA-US-KY-FEDSCREEK', 'FALSE', '', '', '') (42533, 'STANDARD', 'FERGUSON', 'KY', 'PRIMARY', '37.06', '-84.59', 'NA-US-KY-FERGUSON', 'FALSE', '429', '761', '9555412') (40022, 'STANDARD', 'FINCHVILLE', 'KY', 'PRIMARY', '38.15', '-85.31', 'NA-US-KY-FINCHVILLE', 'FALSE', '437', '839', '19909942') (40023, 'STANDARD', 'FISHERVILLE', 'KY', 'PRIMARY', '38.16', '-85.42', 'NA-US-KY-FISHERVILLE', 'FALSE', '1884', '3733', '113020684') (41743, 'PO BOX', 'FISTY', 'KY', 'PRIMARY', '37.33', '-83.1', 'NA-US-KY-FISTY', 'FALSE', '', '', '') (41219, 'STANDARD', 'FLATGAP', 'KY', 'PRIMARY', '37.93', '-82.88', 'NA-US-KY-FLATGAP', 'FALSE', '708', '1397', '20395667') (40935, 'STANDARD', 'FLAT LICK', 'KY', 'PRIMARY', '36.82', '-83.76', 'NA-US-KY-FLAT LICK', 'FALSE', '752', '1477', '14267237') (40997, 'STANDARD', 'WALKER', 'KY', 'PRIMARY', '36.88', '-83.71', 'NA-US-KY-WALKER', 'FALSE', '', '', '') (41139, 'STANDARD', 'FLATWOODS', 'KY', 'PRIMARY', '38.51', '-82.72', 'NA-US-KY-FLATWOODS', 'FALSE', '3692', '6748', '121902277')

	Image
	
## The largest zip code number in zipcodes_one is:

	(47750,) Images
	
## The smallest zip code number in zipcodes_two is:
(38257,)
	Image
	
## Thanks

I worked this project with our tutor Abdirizak kulmiye. Sources https://docs.docker.com/compose/install/ https://mariadb.com/kb/en/mariadb-maxscale-25-simple-sharding-with-two-servers/ https://docs.docker.com/compose/compose-file/ https://github.com/Zohan/maxscale-docker https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04 https://docker-curriculum.com/#what-are-containers-
