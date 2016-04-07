Why do we need the Metadata subsystem. In fact every database management systtem
can be logically divided into storage of the data itself, and storage of the metadata - the information about what data we have, what its semantics, where it is stored etc.
Our system is not exceptions. We need to know what tabkes we have, what is thier structure and how they are distributed among cluster nodes.  We want to know what is "network proximity" between nodes, in order to optimize network bandwith usage.


Information mentioned above is needed for the following cases:
-Query validation. OpenDremel system got the query, related to some table and some columns within the table. We should validate that table indeed exists and it do contain mentioned columns.
- Query execution planning - we wants to know what are nodes where peaces of the table (tablets) are seating.
- new tablets are added to the table, we want to register it.

To give some more precise definition we can define that we are going to store in the metadata:
Tables with thier structure,
List of tablets per table,
List of nodes in the cluster,
Bandwith available between node pairs.
Distribution of all tablets among nodes. Note that some tablets can sit in more then one node.

We can enlist other subsystems who will be clients of this one:
- Schema vier. This subsystem will visualaize what we have in our DB
- Query planner. This subsystem will create execution plan.
- Query dispatcher. This subsystem will manage query execution process and need to know what are nodes where relevant data is sitting.
- Data loader. This module will load data into the system, and register it with the metadata subsytem.


Design decisions to be made.
For now we can see two main approaches to this subsystem design. I will enlist both, and waiting for your comments about them.
<br><b>Persisttent database approach.</b> We can design RDBMS which will be designed after the data model described above. It is strightforward approach. Main disadvantage is a risk of desinchronization between what we have in the cluster and what we have in this database.<br>
<br>
<b>Self discovery approcach </b>
During startup / periodically system can scan all storage available on all nodes and rediscover all metadata. In this case Tablets will ned contain their schema. This approache looks more robust.<br>
<br>
Your comments are required!