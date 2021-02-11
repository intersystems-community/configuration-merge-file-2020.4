# Configuring SQL parameters

This is another example on how any CPF parameter can be tune. With this example we focus on SQL configuration.
It builds on the previous example in directory `../1-Configuration_Memory_Buffers` so if you are unsure on how things works, please see the README in that directory.

## Considerations
In order to focus on the SQL parameters, the memory configurations parameters have been commented out.

Again, use the `start.sh` and `stop.sh` scripts to run & remove the Docker Compose instance and verify the example.

Check how the SQL paremters specified in the `config-merge-file.conf` were effectively merged and used to configure the SQL state of the IRIS instance
- check the `iris.cpf`  of the running instance
  - from the $WDIR try `cat ./iris.sys.d/iris.cpf | more`  
- check the parameters via an IRIS session or via its system management portal
  - ` docker exec -it 1_iris_1 iris session iris`  
  - `http://localhost:9012/csp/sys/utilhome.csp`  (_SYSTEM/SYS)


Don't forget to stop and remove it all with the `./stop.sh` script.
