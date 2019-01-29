# OpenAIS
Discussion, documents and concepts regarding the results of the OpenAIS Lighting IoT Control project
OpenAIS was a project that created an IoT-to-the-node solution for professional grade lighting conrols (2014-2018)
OpenAIS Project was co-funded by EU, and performed by Philips Lighting (now Signify), Zumtobel, Tridonic, Johnson Controls, ARM, NXP, Imtech(Be) the scientific partners TU/E and TNO.
Results have been verified by a subtantial scale demonstrator in Eindhoven (Office type floor, 400 luminaires, 1200 light points, presence detectors, light sensors and manual buttons, connectzed through RF and LAN/PoE.
Main challenge was to master bandwidth issues, instantaneous reaction, synchronicity, and resilience when working strictly with IP to the node.
Communication was based strictly on CoAP, using IPv6 including multicast.
Main result: OGC, Open Group Control, allowing to control group Objects that are distributed at various nodes massively in parallel. Bandwidth issues that arize with synchronized status reports are fully dealt with, overall band usage can be controled by parameters.
