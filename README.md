# docker-linux-codeigniter-mysql
Docker with Linux, CodeIgniter MySQL set up

Steps for executing :

1. After downloading/cloning the repository, open the docker-compose.yml file in the and change the following parameters.

	**db_data directory will store the MySQL data**
	
	**ciapp directory has the CodeIgniter 3.1 source code**
   
   For services => db & services => ciapp, change the path of the volumes directory according to your set up.


2. Change the MySQL environment variables in docker-compose.yml file if required.


3. Open the terminal and go to the directory where docker-compose.yml is located and run the below command :

   		docker-compose up -d --build

4. Step 3 will download the all the dependencies, install it and set up the docker container. After running the command in step 3, it would start two containers. One for MySQL and another for ciapp. It would also create the ciapp database in MySQL.


5. Run the below command to get the list of running containers :

		docker ps

6. After running above steps successfully, open the browser and run the below url :

		http://localhost:8000/
			
   The default CodeIgniter landing page would be display which shows that everything is setup perfectly.




8. References :

	1. https://codeigniter.com/
	2. https://hub.docker.com/_/php/
	3. https://docs.docker.com/
