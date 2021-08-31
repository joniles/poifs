# POIFS 
The [MPXJ](https://mpxj.org) library uses [Apache POI]
(https://poi.apache.org/) to read the OLE2 compound document format which forms
the basis of Microsoft Project MPP files. MPXJ also uses [IKVM]
(https://www.ikvm.net/) to generate a .Net version of MPXJ and its
dependencies, including POI.

IKVM is not currently under active development, and thus bug fixes and
functionality improvements are not immediately available. This is an issue when
using IKVM to convert POI version 5.0.0 to .Net as POI does not support default
methods in Java interfaces, which POI now uses. This repository was created to
produce a workaround by stripping back POI to leave only the POIFS
implementation (the part required by MPXJ), and then updating the remaining
code to remove the use of default methods. The code now present in this
repository can be compiled into a JAR using `mvn package`, and that JAR can
successfully be converted to .Net using IKVM. This allows the .Net version of
MPXJ to utilize code from POI 5.0.0 and later.