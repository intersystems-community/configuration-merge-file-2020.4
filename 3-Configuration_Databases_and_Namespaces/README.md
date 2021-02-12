# Defining Databases and Namespaces

In this exercise we introduce the new `[Actions]` section of the **configuration merge feature**.  
Any time we need to create, update or delete a resource, the *operations* are specified in this new *Action* section.
Operations are idempotent and leverage the existing InterSystems IRIS internal system API.

In this `config-merge-file.conf` we
- create a database (myappdata) to store the application data (check out ./iris.sys.d/myappdata/) and
- define a namespace (myapp) that uses the above database for data and the existing *user* database as the code holder
  - Your application code should already be present in your container (separation of concerns between code and data). This example illustrates how to create the non-ephimeral IOW persistent database the first time you run the container. Any subsequent run of the container (upgrade) the database operation will be ignored as the resource already exists; the operation is idempotent.
  - Note how the database is created on the host system making it persistent. In your solution you might have a more adequate path to it mounting a fast and resilient block storage device.
  - 

Figuratively we end up with the following namespace and databases implementation:

```
IRIS instance
      Namespace             Databases  

                  |-------- MYAPPDATA (Globals)  
      MYAPP ------  
                  |-------- USER (Routines)  
```



