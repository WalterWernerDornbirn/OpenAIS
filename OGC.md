#  Open Group Communication - OGC
Open Group Communication allows to address a group of identical objects, distributed across various nodes, with a single transfer.
Examples given use the well established LWM2M syntax, fully based on CoAP.

## Basic Concepts:
Using IPv6 multicast allows to address multiple nodes at once.
A single node may have implemented more than one instance of the target object, where not all are part of the grouped objects.
Therefore an additional "application group ID" is introduced that selects the grouped objects.
In OpenAIS, every single object instance is allowed to be part of a single application group only. (this is necessary to allow arbitration of conflicting requests)
An oA group object instance is needed for every application group used by a node. This group object contains
    a "security ID" that points to a securtiy object needed to en- and decrypt the message.
    a "members" list of local object instances, that is used to distribute incoming group messages.
    an "IP address" list of (possibly multicast) IPv6 addresses, that is used to distribute outgoing group messages serially. (Some nodes may not be reachable by multicast, e.g. when behind some sort of firewall or router)
    a security object pointer, that is used to encrypt and decrypt the group message flow. 

## Structure of an OGC message:
With OGC group CoAP messages, the target object instance-ID is replaced by the application group ID. All resource addressing and payload structures remain untouched.

    A standard (LWM2M) URI looks like that: 
        /<object-ID>/<instance-ID>/<resource-ID>
    An OGC CoAP group URI looks like that: 
        /g/<object-ID>/<application group-ID>/<resource-ID>
Note the /g/  separates OGC messages from standard LWM2M messages by creating a different namespace. This is necessagy to make sure the application group ID is not mistaken as instance ID.
Additionally, a "single instance OGC message" was designed, to allow for single instance control using the identical security and authentication mechanisms as the group control uses. This is often needed to add some (restricted) node-to-node communication without adding the need for complex server structures, e.g. for corrections after group messages that have been misinterpreted or missed by singel objects.

    An OGC CoAP single instance URI looks like that: 
        /s/<object-ID>/<instance-ID>/<resource-ID>
Again /s creates an additional namespace, that allows implementation independently from LWM2M (or any other framework).

## Security 
OGC transfers are strictly limited to operational content with immediate action (Level 2). No parametrization or alike that is part of device or data management may occur, any OGC request that is above level 2 needs to be discarded at the reception.  However, also this restricted level needs substantial security considerations, as privacy and usability depend on this level.  
Every group is assigned a security object, that is used to allow encryption and decryption of the messages. Note that this includes cross group protection, as a receiver that tries to use a differnet security for this group will not be able to tranmit to or receive from the group.
Note that the security ID has been defined as part of oscore definition. It is mandatory that the security ID used for oscore is checked to be identical with the one given in the group definition.
All key and authentification handling is done using the "hosting framework" definitions, and well established methods.
