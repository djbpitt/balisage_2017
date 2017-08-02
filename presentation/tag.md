% Text as Graph: It’s more than just overlap!
% Ronald Haentjens Dekker and David J. Birnbaum
% Balisage: The Markup Conference, August 2017

____

# Text is multidimensional

<!-- <style>
img { width:100%; height:auto; }
</style>
-->

<img style="width: 70%; height: auto;" class="three-d" src="../Balisage-1-3-xsl/3d_new_perspective.png"/>

<!--
I propose that text, in essence, could be seen as this [show 3D visualization] 

Excerpt of:
The Hunting of the Snark (An Agony in 8 Fits) is a poem written by English writer Lewis Carroll.
-->

____

# Goal

* Academic Research and Development project
* New model for textual data containing
  generic markup
* Able to deal with many textual phenomena 
* Suitable for (focus on) mixed content
* Multiple layers of annotation 
* Either manual or machine assisted
* Separation of model and application layer

____


# Textual phenomena I

* Overlap (multiple hierarchies) 
* Discontinuity

More to come...


____

# Overlap (multiple hierarchies)
 
Percy Bysshe Shelley, “Ozymandias”

> Who said — **“Two vast and trunkless legs of stone  
Stand in the desart....** Near them, on the sand

```xml
<line>
	<phrase>Who said —</phrase>
	<phrase>“Two vast and trunkless legs of stone
</line>
<line>
	Stand in the desart….</phrase>
	<phrase>Near them,</phrase>
	<phrase>on the sand</phrase>
</line>
```
____

# Multiple hierarchies: projecting two trees over the same text nodes

<img src="../Balisage-1-3-xsl/ozymandias_trees_transparent.png" width="99%"/>

____



# Discontinuity in XML

Lewis Carroll, *Alice in Wonderland*

> Alice was beginning to get very tired of sitting by her sister on the bank, and of having nothing to do: once or twice she had peeped into the book her sister was reading, but it had no pictures or conversations in it, **“and what is the use of a book,”** thought Alice **“without pictures or conversation?”**
 
```xml
<p>Alice was beginning to get very tired of sitting by her sister 
on the bank, and of having nothing to do: once or twice she had 
peeped into the book her sister was reading, but it had no pictures 
or conversations in it, <q>and what is the use of a book,</q> 
thought Alice <q>without pictures or conversation?</q></p>
``` 

<!--
Any XML processor knows that XML start and end tags go together. In TEI attributes needs to added to indicate that the two go together. The application needs to deal with this difference.
-->
____

# Model: Text as Graph

## Terminology

* **Text:** comparable to XML text nodes (Document node is there to know where to begin)
* **Markup:** comparable to XML elements
* **Annotation:** comparable to XML attributes, except that 1) annotation text may have markup, and 2) annotations on annotations are permitted

## Components

TAG is a directed **hypergraph** model

* **Nodes** (Document, Text, Markup, Annotation)
* **Edges** (one-to-one; textual order)
* **Hyperedges** (one-to-many, many-to-one; markup and annotation)

Operations in TAG are operations on sets of nodes and edges

<!-- explain what a hypergraph is -->
<!-- there is a lot of accumulated knowledge about reasoning over and operation with sets -->
____


# TAG in 3D

<video height="80%" controls>
  <source src="animation/output.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

____


# TAG Flyby

<video height="80%" controls>
  <source src="animation/snark-fly.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

____

# Overlap (multiple hierarchies) in TAG

Percy Bysshe Shelley, “Ozymandias”

> Who said — **“Two vast and trunkless legs of stone  
Stand in the desart....** Near them, on the sand

<img src="../Balisage-1-3-xsl/ozymandias_hypergraph_transparent.png" width="99%"/>

<!-- ai the hierarchies are not really all that visible here, since the "dominate" relation is not used. Say something here about the difference between containment and dominance? -->

____

# Discontinuity in TAG

Lewis Carroll, *Alice in Wonderland*

Alice was beginning to get very tired of sitting by her sister on the bank, and of having nothing to do: once or twice she had peeped into the book her sister was reading, but it had no pictures or conversations in it, “and what is the use of a book,” thought Alice “without pictures or conversation?”

<img src="../Balisage-1-3-xsl/discontinuity_hypergraph_transparent.png" width="99%"/>

____

# Textual phenomena II

* White space as crypto-overlap
* Datatyping and artifactual hierarchy
* Main-text content and annotation content
* Scope of reference

____

# White space as crypto-overlap

William Shakespeare, Sonnet #71

```xml
<line>
	<foot>No l<stress>o</stress>n</foot><foot>ger m<stress>ou</stress>rn</foot>
	<foot>for m<stress>e</stress></foot>
	<foot>when <stress>I</stress></foot>
	<foot>am d<stress>ea</stress>d</foot>
</line>
```

The following pseudo-XML is not well formed:

```xml
<line>
	<foot><word>No</word> <word>l<stress>o</stress>n</foot><foot>ger</word>
		<word>m<stress>ou</stress>rn</word></foot> 
	<foot><word>for</word> <word>m<stress>e</stress></word></foot>
	<foot><word>when</word> <word><stress>I</stress></word></foot>
	<foot><word>am</word> <word>d<stress>ea</stress>d</word></foot>
</line>
```

# White space as crypto-overlap in TAG

<img src="../Balisage-1-3-xsl/feet_transparent.png" width="99%"/>
____

# Data typing causes artifactual hierarchy in XML

```xml
<title><name>Romeo</name> and <name>Juliet</name></title>
```

![](../Balisage-1-3-xsl/romeo_xml_transparent.png)

____

# Data typing in TAG

![](../Balisage-1-3-xsl/romeo_hypergraph_transparent.png)

____



# Two challenges of footnotes in XML

1. Main text vs annotation text
1. Scope of reference

> Textual content in TAG is expressed by nodes with a **type** value of “text”, each of which represents a segment of textual content (Text nodes may also be empty). The order of the text is stored as directed regular (one-to-one) edges between pairs of Text nodes; this chain begins at the Document node, which points to the first Text node, and a single, unbroken chain connects all Text nodes in the document except those in annotations.<sup>23</sup>

```xml
<p>Textual content in TAG is expressed by nodes with a <strong>type</strong> 
value of “text”, each of which represents a segment of textual content 
(Text nodes may also be empty). The order of the text is stored as directed 
regular (one-to-one) edges between pairs of Text nodes; this chain begins at 
the Document node, which points to the first Text node, and a single, 
unbroken chain connects all Text nodes in the document except those in 
annotations.<fn><p>[Haentjens Dekker and Birnbaum 2017]</p></fn></p>
``` 
 
1. Is the footnote text part of the main text?
1. Is the footnote on the last sentence, the last two sentences, or the entire paragraph?

____

# Footnotes in TAG

<img src="../Balisage-1-3-xsl/note_transparent.png" width="99%"/>

1. Content of footnote is not part of the main content of the document.
2. Scope of footnote is represented by the hyperedge pointing to the anonymous Markup node.  


____

# Prototype implementation

* Alexandria Markup is a prototype implementation of TAG
* Client/server architecture
* REST protocol
* Server is written in Java
* Clients available in Java and Python
* Open source Apache license
* Able to import files encoded in LMNL Sawtooth syntax
* Able to import files encoded in TexMECS syntax
* Query language in early stage of implementation
* Schema language validation in early stage of development
* TAG portal: <https://github.com/HuygensING/TAG>

____

# Key TAG features

1. Represents textual properties at the level of the model and in a natural and idiomatic way
1. Addresses several textual phenomena that cannot all be represented in other models without workarounds or dependence on markup semantics at the application level
1. Does not impose a hierarchy, but allows one or more
1. Currently supports one order, but could be extended to allow unordered content or multiple orders

____

# Thank you!

Ronald Haentjens Dekker  
Head of Research and Development and Software Architect  
Huygens ING  
ronald.dekker@huygens.knaw.nl

David J. Birnbaum  
Professor and Chair  
Department of Slavic Languages and Literatures, University of Pittsburgh  
djbpitt@gmail.com  
<http://www.obdurodon.org>

