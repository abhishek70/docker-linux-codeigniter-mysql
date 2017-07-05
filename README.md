# docker-linux-codeigniter-mysql
Docker with Linux, CodeIgniter MySQL set up

Steps for executing :

1. After downloading/cloning the repository, open the docker-compose.yml file in the and change the following parameters.

	db_data directory will store the MySQL data
	ciapp directory has the CodeIgniter 3.1 source code
   
  For services => db & services => ciapp, change the path of the volumes directory according to your set up.


2. Change the MySQL environment variables in docker-compose.yml file if required.


3. Open the terminal and go to the directory where docker-compose.yml is located and run the below command :

   docker-compose up -d --build

4. Step 3 will download the all the dependencies, install it and set up the docker container. After running the command in step 3, it would start two containers. One for MySQL and another for ciapp. It would also create the ciapp database in MySQL.


5. Run the below command to get the list of running containers :

		docker ps

6. CodeIgniter store the session in the database so its require to create the table in ciapp databases in MySQL. Run the below command :

		docker exec -it CONTAINER-ID mysql -uroot -p

	 Replace CONTAINER-ID with the container Id of the MySQL that would be available from the command in step 5. After running the above command it would ask for the root password which is set in the docker-compose.yml file in environment variables.

	```
	CREATE TABLE IF NOT EXISTS `ci_sessions` (
         `id` varchar(128) NOT NULL,
         `ip_address` varchar(45) NOT NULL,
         `timestamp` int(10) unsigned DEFAULT 0 NOT NULL,
         `data` blob NOT NULL,
         KEY `ci_sessions_timestamp` (`timestamp`)
	);
	```
	```
	// When sess_match_ip = FALSE
	ALTER TABLE ci_sessions ADD PRIMARY KEY (id);
	```

7. After running above steps successfully, open the browser and run the below url :

		http://localhost:8000/
			
		The default CodeIgniter landing page would be display which shows that everything is setup perfectly.


