# Configuring Memory Buffers

In this directory we have a simple example automating the most common operation of configuring memory buffers.


## Considerations
The solution, like all the rest found in the parallel directories, runs a *docker-compose* definition.
The main file to view is the `config-merge-file.conf` that contains the parameters we want to configure our instance with.
The *configuration merge file* can be called anything you want.

Notable:  
- Just like the `iris.cpf`, the **configuration merge feature**, uses the exact same fields as input parameters for configuring the IRIS instance. A merge operation is run for the user automatically as long as the `ISC_CPF_MERGE_FILE`  environment variable is set.
- In this file, for this example, there are only two main sections for simplicity, the
  - [Startup] and 
  - [config] sections  
however, any `iris.cpf` parameter can be configured.

- Note the hashed password that is used to change the System users' default password.
  - Although you can generate the password with an IRIS Instance, you can use the container image `intersystems/passwordhash` from [InterSystems Container Registry](https://containers.intersystems.com) to gain a hashed password simply and interactively with  
    - `docker run --rm -it intersystems/passwordhash:1.0`
- In the **configuration merge file** we are changing 5 memory related parameters
  1. Global buffers
  2. RO\outine buffers
  3. Error log entries
  4. Gmheap and 
  5. the size of the lock table


## How to run it
You can run the `start.sh` script to start the Docker Compose definition. Then check how the paremters specified in the `config-merge-file.conf` were effectively merged and used to configure the state of the IRIS instance specified in the `docker-compose.yml`.
- check the iris.cpf of the running instance and 
- check the parameters via an IRIS session or via its system management portal

Please note how the envrionment variable `ISC_CPF_MERGE_FILE`
- triggers the merge operation and 
- points to the file that carries the declaration of the parameters to tune

In our case we have 
`ISC_CPF_MERGE_FILE=/ISC/config-merge-file.conf`

To stop the example, simply run the `stop.sh` script.
