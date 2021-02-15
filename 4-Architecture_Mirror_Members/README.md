# Defining a canonical mirror architecture topology

With this declaration we tell each IRIS instance to configure itself according to an architecture topology.
Here we define the canonical **InterSystems IRIS mirror technology** that is defined as a two instances tightly coupled members. There is also a third component that aids in the leader election and avoids the split-brain situation, that is, the Arbiter.

The two mirror technology members are called
- the primary - the service that comes up as the main, primary, active service and
- the backup - the secondary, stand-by service

The definitions for the two members are simple
- Primary member
  - `MirrorSetName=mymirror`
  - `MirrorMember=primary`
- Backup member
  - `MirrorSetName=mymirror`
  - `MirrorMember=backup`
  - `MirrorPrimary=10.0.0.11`  

Because IRIS instances are self-aware and self-configuring, we provide a different configuration merge file for each instance telling them the initial role (primary or backup) that we expect them to start with. Those initial roles can subsequently be swapped as the service fails-over and back again. When those operations happen,roles are automatically set by the systems as they dialogue with eachother and coordinate things with the Arbiter.

Please note how in the [Actions] section of the configuration definition, the database we create (as we did in the previous example (directory ../3-Configuration_Databases_and_Namespaces) is now marked as a *mirror database*. That means that any operation performed on that database is replicated or mirrored from the *primary* member to the *backup* member of the mirror pair.

Figuratively we end up with the following
- architecture topology and
- mirrored database

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

