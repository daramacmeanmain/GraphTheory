# Graph Theory - GMIT Timetable Project

This is my Neo4j database for graphing a timetable for GMIT. 

The database stores information for the following items

* Lecturers
  * Ian McLoughlin, Damien Costello, etc
* Subjects
  * Graph Theory, Mobile Apps, etc
* Rooms
  * 994, CR5, etc
* Class Groups
  * A, B, C
* Times
  * 9:00, 10:00, etc
* Days
  * Monday, Tusday, etc
  
## Nodes

Each item is represented by a node type in the graph, with each node having a `name` property to identify it, e.g. `Lecturer` has a node with the name `Ian Mcloughlin`. The node in question is created using `CREATE (im:Lecturer{name:"Ian Mcloughlin"})`. 

This `CREATE` query is then used to add each node in the database. In the end, the database contains 49 different nodes to graph the relevant data.

## Relationships

Each node relates to another in some way. For example, Ian McLoughlin teaches Graph Theory in 0938 at 10:00 on Wednesday. This relationship is formed using the following query 

`MATCH (im:Lecturer{name:"Ian Mcloughlin"}), (gt:Subject{name:"Graph Theory"}), (a938:Room{name:"0938"}), (ten:Time{name:"10:00"}), (wed:Day{name:"Wednesday"})
CREATE (im)-[:TEACHES]->(gt)-[:IN]->(a938)-[:AT]->(ten)-[:ON]->(wed)`

Thus, the relevant nodes are joined together.

## Screenshot of Final Graph

![alt text](http://i.imgur.com/RnGnWQW.png "Graph Screenshot")
