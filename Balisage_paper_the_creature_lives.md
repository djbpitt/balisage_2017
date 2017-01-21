#### Rationale for moving beyond XML

Textual data is unstructured. Markups needs to be added to extract information from it. The most popular markup format to store textual data and markup is XML. XML follows a hierarchial model that allows one to add structure to a file. This works well for dividing text into chapters and paragraphs. However there are limitations.

 Adding a second hierarcy is difficult, since XML markup syntax requires that the last opened tag is closed first. Adding the structure of the pages for example overlaps with the stucture of the chapters and paragraphs.
This can be worked around by adding a second hierarchy as milestones instead of start and end elements.

The problem here is that one hierarchiy is handled differently from the second hierarchy.
The leading hierarchy is modeled using full start and elements.

Modelling multiple hierarchies is possible in XML, but difficult because the second or third etc hierarchy needs to be modelled differently from the first hierarchy.
This also leads to challenges when querying or transforming the data contained in the file.

There are many real use cases where there are multiple hierarchies present in the data:
poetry, stage plays.

### LMNL markup file format
The LMNL markup file format removes the constraint that the last opened has to be closed first. That means that it is possible to model overlapping hierarchies in LMNL. To be more precise, it is possible to model annotations with one hierarchy, multiple hierarchies or no hierarchy at all. This allows for a great freedom to model all kinds of information on textual content. This is great from a content perspective. However LMNL is more expensive from a computational perspective.

### Conceptual model

The conceptual datamodel behind is XML is the Document Object Model (DOM). The DOM represents a tree based data structure. The data model behind LMNL is different, in that it is based on ranges, based on offsets on textual content.


### Text as a graph
This paper proposes to use a different data model than trees or ranges. It proposes to use a graph based model, we call text as graph (TAG).
Graph models for text have been proposed before (GODDAG), but the model proposed in this paper differs in the fact that not just a directed graph is used, but a directed graph is used in combination with a hypergraph.

 

