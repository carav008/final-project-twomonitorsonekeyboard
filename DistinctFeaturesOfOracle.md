# Distinct Features of OracleDB
In this file we are going to go in depth into some of the features that make Oracle DB stand out.


## Multitenant Architecture
### What is it?
Multitenant Architecture is the idea of having a Container Database(CDBs) with sub databases called Pluggable databases(PDBs). What
does this exactly mean? It means that a container database will be allowed to contain anywhere from 0 to n PDBs. Well what in the world is a PDB though? A PDB is a portable collection of schemas<sup>[1](#schema)</sup>, schema objects<sup>[1](#schema)</sup> and non-schema objects<sup>[1](#schema)</sup>

![](/images/MultitenantArchitecture12c.jpg)

*Figure 1: Displays the Multitenant Architecture explained by Oracle*


Figure 1 shows the process of the Oracle CDB and PDB interaction with all other files of the database but for now we will concentrate on the larger aspect of things. A simpler more straight to the point option, is the figure we created below.

![](/images/MultitenantArchitectureBC.jpg)

*Figure 2: a bigger picture view of the Multitenant Architecture*

One aspect to note is that there can only exist one root database, the CDB that will hold Oracle metadata needed for it to run correctly while PDBs store user defined metadata. Oracle will additionaly contain a seed PDB that will be the template provided by Oracle for the creation of any other PDBs that could be created. This PDB cannot be changed or modified.


### Benefits
Before OracleDB 12c, the database structure consisted of non-CDBs which are just regular databases, similar to what PDBs are now. Now with the Multitenant Architecture non-CDBs seem almost obsolete.

Read some of the benefits that are produced by it.
* **Database Consolidataion**<sup>[2](#dbc)</sup> is now made easier when one CDB runs in the SGA(system global area) because it is only running a single set of background decreasing the cost of computation and memory resources.
* It is easy to unplug<sup>[3](#unplug)</sup> a PDB from one CDB to another, transferring all contents with it.
* The advantage of separation of privileges meaning that:
    * CDB :arrow_right: PDB: a user that has access to the CDB will have access to any PDB.
    * PDB :arrow_right: CDB: a user with access to only to certain PDB's doesn't have access to entire CDB.
    * PDB1 :no_entry_sign: PDB2: This also means that a user who only has access to a certain PDB1 will/cant have access to PDB2.
* Patching/Updating and Backing up any content is made easier because you need now change only 1 CDB to update any amount of PDBs within it (vs updating multiple non-CDBs).

Lastly if you have any confusion Oracle offers this cool interactive Mutltitenant Architecture model [here](http://www.oracle.com/webfolder/technetwork/tutorials/obe/db/12c/r1/poster/OUTPUT_poster/poster.html#)

## Pl/SQL and Java
A unique feature of OracleDB is the way it allows PL/SQL and Java to interact. You can call Java programs using SQL and call SQL in Java programs. This is the Server side programming aspect of Oracle DB. Although we didn't do much exploration of this there are multiple resources online! Here are two:

* [Intro to Java in OracleDB]https://docs.oracle.com/database/121/JJDEV/chone.htm#JJDEV01000)

* [DB Java Dev Guide](https://docs.oracle.com/database/121/JJDEV/toc.htm)

* [Server Side Programming](https://docs.oracle.com/en/database/oracle/oracle-database/12.2/cncpt/server-side-programming.html#GUID-D4A154D2-DF56-45DA-863C-BED5DA6BDA34)


<footer>
<a name="schema">1</a>: See reference Glossary in [works cited][workscited] for definitions [↩](#schema)

<a name="dbc">2</a>: The process of consolidating data from multiple databases into one database on one computer.[↩](#dbc)

<a name="unplug">2</a>: Meaning to close the connection between a pluggable database and its container database[↩](#unplug)
</footer>


[workscited]: (WorksCited.md)
