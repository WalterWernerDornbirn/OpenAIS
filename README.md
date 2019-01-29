# OpenAIS
Discussion, documents and concepts regarding the results of the OpenAIS Lighting IoT Control project

About OpenAIS: 
   OpenAIS was a project that created an IoT-to-the-node solution for professional grade lighting conrols (2014-2018)
   The OpenAIS project was co-funded by EU, and performed by Philips Lighting (now Signify), Zumtobel, Tridonic, Johnson Controls, ARM, NXP, Imtech(Be) the scientific partners TU/E and TNO.
   Results have been verified by a subtantial scale demonstrator in Eindhoven (Office type floor, 400 luminaires, 1200 light points, presence detectors, light sensors and manual buttons, devices connected through RF and LAN/PoE.)
   Results are published on a public website, that may get offline one day: http://www.openais.eu 

Main challenges when using using IP-to-the-node:
    master bandwidth issues when operating a large mixed PHY network including (slow) meshed RF, 
    create instantaneous reaction to manual interaction, e.g. turning on/off or start/stop dimming for a larger group.
    allow for good synchronicity e.g. when executing a scene command
    create a resilient system that remains operable when more central components fail or get disconnected.
    
Main achievements:
    
    OGC, the Open Group Communication for CoAP:
        Groups objects distributed on nodes
        Fast and parallel operation using IPv6 mulitcast. 
        Operates a direct node-to node communication without central servers (Commissioing and initialization still needs central servers)
        Provides out-of-the-box networked functionality before commissioning takes place
        Limits the peak network load and allows to adjust the everage load on the network.
        Adds command and local interaction to LWM2M or other IoT frameworks that may be used in parallel for device and data management.
        
    oA LWM2M professional lighting object hierarchy
        Controling the operation of OGC.
        Arbitrating conflicting access to a single actuator object at the final node.
        Maintaining group communication interoperability beyond vendor differentiation.
        Versatile and unlimited grouping and scene handling (including means for dynamic scenes).
        Providing support for multiple signal filter, threshold and timing characteristics for sensors reporting to different groups. 
        Including the typical features expected from professional lighting actuator and sensor objects.
        Hierarchical Control setting with fallback-to-local when more central control fails.
        Compressed reporting system reducing the number of transfers needed.
        Means to handle user interaction and authentication through the control objects, avoiding the need of direct user access to final nodes.
    
This branch is created to make some of the concepts avcailable through GitHub. We are sorry that there is no code provided, as the code itself remains property of the executing companies and cannot be shared here.
