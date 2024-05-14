## **What is PostgreSQL:**
-   Open-source relational database system released in 1996
## **Key Features of PostgreSQL:**
-   Relational Database management system
-   Free and open-source
-   Support all OS
-   ACID compliant
-   Support MVCC(Multi Version Concurrency Control){Multiversion concurrency control (MVCC) is a database optimization technique. MVCC creates duplicate copies of records so that data can be safely read and updated at the same time.}
-   Support user defined datatypes
-   Support audio,video,image,and graphical data storage
-   Supported by all the programming languages
## **Postgre Installation:**
- ### Install Docker:
    -  Go to Docker.com
    -  Click on Download Docker
    -  Install Docker and agree the license
- ### Set up postgres in Docker
    -  Go to hub.docker.com and create an account
    -  Search for Postgres in docker search 
    -  Open docker official image of Postgres
    - Two command from this page are required
      1. docker pull command to pull postgres image
      2. Docker run command to create the postgres
    - Step 1: Pull the Image 
        Open command prompt and write: docker pull postgres
        #
          docker pull postgres
    - Step 2: Create the container
        #
          docker run --name my_postgres -d -e POSTGRES_PASSWORD=postgres -p 5432:5432 -v D:/postgres:/var/lib/postgresql/data postgres
        - --name my_postgres : This option gives a name (postgres_img) to our Docker container.
        - -d: This option runs the container in detached mode, meaning it runs in the background without blocking the terminal, and it prints the container ID once it's done.
        - -e POSTGRES_PASSWORD=postgres: This sets an environment variable (POSTGRES_PASSWORD) inside the container and assigns it the value postgres. This is the password you'll use to access the PostgreSQL database.
        - -p 5432:5432: This option exposes port 5432 on the container to the same port on the Docker host machine. Port 5432 is the default port for PostgreSQL, and exposing it allows external clients to connect to the PostgreSQL database running in the container.
        - -v D:/postgres:/var/lib/postgresql/data: This option maps a directory on the Docker host machine (D:/postgres) to a directory inside the container (/var/lib/postgresql/data). This mapping enables persistent storage for the PostgreSQL data directory. Any data written to the PostgreSQL data directory inside the container will be saved to the specified directory on the host machine (D:/postgres), ensuring data persistence even if the container is stopped or restarted.
        - postgres_image: This is the name of the Docker image used to create the container. In this case, it's the PostgreSQL image, which contains the necessary files and configurations to run a PostgreSQL database server.
      - Step3: Run the command
            - Run above command
            - Go to Desktop home 
            - There we can see the created image of postgre
## **Connect to PostgreSQL Database using PSQL** 
### Start the Dcoker
Click on docker desktop app icon and start the docker
### Start the container
-    Two methods
        -    Step 1: Using desktop run icon
              -    Check on box and click on run button
        -    Step 2: Using CLI command
             #
                 docker start my_postgres
### Connect to container
-    Default CLI to work with PostgreSQL is PSQL
-    Open terminal and write the command
  #
      docker exec -it my_postgres psql -U postgres
-   "docker exec" command is used to execute commands within a running Docker container.
-   We can use the “-it” option together, which is a combination of two options. The “-i” option tells the Docker to allocate a pseudo-TTY for the command, and the “-t” option tells the Docker to create an interactive terminal session.
-   We need to pass the container name and the PostgreSQL default command-line interface “psql”.
-   We can also pass the desired username using the “-U” option.
-   Running this command succeeds the connection to PostgreSQL
### intial command
    \du
-    This is a meta command shows you name of all the users that are available on your server
  
## **Connect PostgreSQL with VS Code**
- To connect to PostgreSQL, make sure you have properly installed VS Code on your machine.
### Installing the SQLTools Plugin For PostgreSQL
-    Step 1: Open your VS Code.
-    Step 2: Go to Extensions and search for ‘SQLTools’ extension.
-    Step 3: Install the ‘SQLTools’ extension by Matheus Teixeira.
-    Step 4: Once installed, locate the ‘SQLTools’ extension in the left-hand side extension bar, identifiable by its database-like icon.
### Installing the SQLTools PostgreSQL/Cockroach Driver
-    Step 1: Go to Extensions and search for ‘SQLTools PostgreSQL’ by Matheus Teixeira.
-    Step 2: Install the ‘SQLTools PostgreSQL/Cockroach Driver’ extension.
-    Step 3: Ensure that both the ‘SQLTools’ extension and the driver are successfully installed.
### Setting Up the Connection Assistant Form
-    Go to the SQLTools extension in the extension bar.
-    Click on ‘Add New Connection’ and select ‘PostgreSQL’.
-    Complete the Connection Assistant form using the installation string information:
    -    Enter a desired connection name.
    -    Leave the Connection Group field empty.
    -    Keep the Connect String set on “Server and Port”.
    -    Specify the Server address, using “localhost” if PostgreSQL is installed on the same machine or the IP address of a remote server.
    -    Use the default port number, 5432, for the Port field.
    -    Enter the name of the database to which you want to connect, using all lowercase letters for the default database, “postgres.”
    -    Provide the default username, “postgres,” in lowercase letters.
    -    Set the Use Password value based on your preference for security.
    -    Enter the password assigned during installation.
    -    Leave the remaining fields with their default values.
-    Test the connection to ensure its success.
### Handling Errors and Establishing Connection
-    If any errors occur, ensure that your Docker container for PostgreSQL is running. Direct installations should not encounter similar issues.
-    Once any errors are resolved, save the connection settings.
-    From the connection panel, select the newly created connection, right-click on it, and choose “Connect.”
-    This action opens a fresh SQL worksheet, ready for query execution.
### Running SQL Queries
-    Within the SQL worksheet, write and execute your SQL queries.
-    As an example, let’s check the current user name with which we are connected:
#
    SELECT current_user;
-    Execute the query by clicking the “Run On Active Connection” button.
## **TABLSESPACE in PostgreSQL**
-    TABLESPACE is logical name given to a specific location in a disk drive
-    It is a storage area for various database objects such as files, tables, views, index etc
### Advantages of TABLESPACE in PostgreSQL
-    All database objects remain organized under a named location. So, database backup and recovery is easy.
-    Database Performance: More frequent data files can be located on a faster device where as less frequent database can be located on a slower device.
### Default TABLESPACE
-    By default PostgreSQL has 2 default TABLESPACEs
#
    pg_default
-    This TABLESPACE holds user data like template 0 and template 1 databases
#
    pg_global
-    This TABLESPACE holds global database data like system catalogs.
### Syntax for creating TABLESPACE in PostgreSQL
#
    CREATE TABLESPACE tablsespace_name
    OWNER user_name
    LOCATION directory_path
-    Note:
      -    Can write in Capital or Small letters
      -    Dont start tablespace name with PG_ it is reserved for PostgreSQL
      -    OWNER is optional , it can be emitted , user who creates or owns this tablespace is owner
      -    Location defines a space on disk drive where we want to create a tablespace
### Create A Directory for Tablespace in PostgreSQL
-    To create a tablespace, it is essential to first create a directory. If you have installed your database directly on your Mac or Windows system, simply create a folder on your system. That’s all you need to do. If you want to set up your database on Docker, Follow the below process to create the directory.
-    Step1 : Start Your Docker
          -    Double-click on the Docker Desktop app to start it
-    Step2 : Start the Postgress Container
          -    Run the container that contains your PostgreSQL Database
          -    To start this container, open your Command Prompt or Terminal and execute the following command: (Note: my container name = my_postgres)
      #
         Docker Start <your_container_name>
         #For Example
         Docker Start my_postgres
-    Step3 : Login as ROOT into bash
          -    To create a directory , access the bash shell with ROOT user
          -    Execute command:
     #
         docker exec --user root -it <container_name> bash
         #For Example
         docker exec --user root -it my_postgres bash    
-    Step4 : Create The Directory For Tablespace in PostgreSQL
          -    create a directory named “tablespace” inside “/home”. 
     #
         mkdir /home/tablespace
-    Step5 : Fix the Permission
          -    execute the following command:
     #
         chown postgres:postgres /home/tablespace
-    Step6 : Set permission on Podtgres Group
          -    After changing the group of our directory from root to postgres,
          -    The next step is to grant “read, write, and execute” permissions to the postgres group.
          -    Execute the following command:
     #
         chmod g+rwx /home/tablespace
### Command to see all tablsepace created
    \db
-    For detail information
  #
    \db+
## **Create Database in PostgreSQL**
### Create Database Command:
    CREATE DATABASE database_name
    OWNER = owner_name
    TEMPLATE = template
    ENCODING = encoding			
    LC_COLLATE = collate			
    LC_CTYPE = ctype
    TABLESPACE = tablespace_name;
-    database_name : specifies name of database
-    owner : specifies who owns the databse, By default owner is user who executes "CREATE DATABASE" command
-    template : specifies a template for creating database, By default, template1
-    encoding : specifies character set for database, determine how characters are stored and retrieved
-    LC_COLLATE : LOCALE COLLATION , specifies sorting order of text within database . For instance, if set to English, words such as “cherry,” “banana,” and “apple” will be sorted alphabetically as “Apple,” “banana,” and “cherry.” However, if a different language is chosen, the sorting will differ accordingly. By omitting this parameter, the LC_COLLATE value from the template database will be inherited.
-    LC_CTYPE : LOCALE CHARACTER CLASSIFICATION :     governs categorization of characters within database. For instance, in English, the letters ‘a,’ ‘e,’ ‘i,’ ‘o,’ and ‘u’ would be classified as vowels. However, with a Spanish setting, the classification would differ accordingly.
-    TABLESPACE : Specifies a space where database files are stored in disk
### Connect with PostgreSQL:
-    Step1 : Connect to postgre Docker:
#
    Docker exec -it postgres_img psql -U postgres
-    Step2 : Create the Database
#
    CREATE DATABASE library
    OWNER = postgres
    TEMPLATE = template0
    ENCODING = UTF8
    LC_COLLATE = 'en_US.utf8'
    LC_CTYPE = 'en_US.utf8'
    TABLESPACE = ts_users;
-    template0 - a default twmplate
-    UTF8 - a unicode standard, widely used standard to represent text in computers
-    en_US.utf8 represent english using UTF-8 encoding
## **Backslash Commands**
- Note: All command start with 'backslash' '\' are called "Meta Commands"
### Check if the database is created or not.
    \l
-    shows all database that are created
### Command to connect with Database
    \c <databse_name>
-or execute 

    SELECT current_databse();
## **ALTER Database Command**
### Rename Database Command:
    ALTER DATABASE <current_database_name> RENAME TO <new_database_name>
### Set or Modify user in databse:
    ALTER DATABASE <current_database_name> OWNER TO <new_user_name>
### Set or Modify default tablespace:
    ALTER DATABASE <current_database_name> SET TABLESPACE <new_tablespace_name>
## **Drop a Database**
### Commmand to drop database:
    DROP DATABASE [IF EXISTS] <database_name>
### Restrictions to drop a database:
  1. Only superuser or owner can drop a database
  2. There should not be any user connected to database that we want to drop, if any terminate the connection before dropping db
    -    Command to terminate
     #
         SELECT * FROM pg_stat_activity WHERE datname='<database_name>';
     -    this shows database where connected to a user
     #
         SELECT pg_terminate_backend(105) FROM pg_stat_activity WHERE datname='<database_name>'; //105 is pid of active connection
- Two scenarios to drop database
  1. Database is idle and no user is connected to it
  2. Database is in use and some users are connected to it
  ## **Create a user**
  ### Create user using "Create User" command
  -    It is a shortcut to create role command
  -    Have priveleges such as "Create" and "Connect"
  #
      CREATE USER <user_name> WITH PASSWORD '<password>';
  -    To connect this user to a specific database , grant connect privelege to user created:
  #
      GRANT CONNECT ON DATABASE <database_name> TO <user_name>;
  -    Grant create privelege to this user on database , which allows permission to user to create objects such as tables , views etc
  #
      GRANT CREATE ON DATABASE <database_name> TO <user_name>;
  ### Create user using "Create Role" command
  -    Create role command doesnt have any default priveleges or permissions
    ## ""Change User Password in PostgreSQL"
  -    Three different ways:
  ### 1.Using Pormpt
  -    Step1: Connect with database superuser
  #
      Docker exec -it postgres_img psql -U postgres
  -    Step2 : Issue '\password' meta-command
  #
      \password <user_name>
  -    Enter new password twice    
  ### 2.Alter Role DDL
  -    Step1 : Connect with database using a superuser , verify by executing following command
  #
      SELECT current_user(); 
  -   Step2 : Write Alter role DDL Command:
  #
      ALTER ROLE <user_name> WITH PASSWORD '<new_password'>
  ### 3.Alter user DDL
    #
      ALTER USER <user_name> WITH PASSWORD '<new_password'>
