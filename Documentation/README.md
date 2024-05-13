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
  ![SampleImage](https://github.com/ShanaSherinIsmayil/PostgreSQL/edit/main/Documentation/Screenshot 2024-05-13 120039.png)
