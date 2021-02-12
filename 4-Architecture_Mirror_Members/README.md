# Defining a canonical mirror architecture topology

With this declaration we tell each IRIS instance to configure itself according to a an architecture topology.
Here we define the canonical InterSystems IRIS mirror technology that is defined as a two members instances with a third component that aid sin the leader election and avoids the split-brain situation, that is, the Arbiter.

The two mirror technology members are called
- the primary - the service that comes up as the main, primary, active service and
- the backup - the secondary, stand-by service


Note, in the [Actions] section of the configuration definition, the database we created in the previous example (directory ../3-Configuration_Databases_and_Namespaces) is now marked as a mirror database. That means that any operation performed on that database is replicated or mirrored from the *primary* member to the *backup* member of the mirror pair.

Because IRIS instances are self-aware and self-configuring, we provide a different configuration merge file for each instance telling them the initial role (primary or backup) that we expect them to start with. Those initial roles can subsequently be swapped as the service fails-over and back again. When those operations happen,roles are automatically set by the systems as they dialogue with eachother and coordinate things with the Arbiter.

In the architecture... ??? - anything else here??


Figuratively we end up with the following
- architecture topology and
- mirrored databases

```
MYMIRROR mirror system 
        PRIMARY member instance
                Database                        
                        MYAPPDATA [mirrored]

        BACKUP member instance
                Database                        
                        MYAPPDATA [mirrored] 

        ARBITER
                leader election / coordinator
```
## Requirements
- a valid InterSystems IRIS key for mirroring

