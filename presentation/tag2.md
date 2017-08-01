% Text as Graph: It’s more than just overlap!
% Ronald Haentjens Dekker and David J. Birnbaum
% Balisage: The Markup Conference, August 2017

____

# Teaser

<img class="three-d" src="../Balisage-1-3-xsl/3d_new_perspective.png"/>

<!--
I propose that text, in essence, could be seen as this [show 3D visualization] 
-->

____

# Goal

* Part of Research and Development project
* Coming up with a new model for textual data containing
  generic markup
* Able to deal with many textual phenomena 
* Suitable for (focus on) mixed content
* Allowing for many layers of annotation 
* Either human made or machine made
* Keeping as much logic as possible out of the application layer

____


# Textual Phenomena I

* Overlap (multiple hierarchies) 
* Discontinuity

More to come...


____

# Overlap (multiple hierarchies)
 
Percy Bysshe Shelley, “Ozymandias”

> Who said — **“Two vast and trunkless lets of stone  
Stand in the desart....** Near them, on the sand

```xml
<line>
	<phrase>Who said —</phrase>
	<phrase>“Two vast and trunkless legs of stone**
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
____

# Model: Text as Graph

## Terminology

* **Markup:** comparable to XML elements
* **Annotation:** comparable to XML attributes, except that 1) annotation text may have markup, and 2) annotations on annotations are permitted

## Components

TAG is a **hypergraph** model

* **Nodes** (Document, Text, Markup, Annotation)
* **Edges** (one-to-one; textual order)
* **Hyperedges** (one-to-many, many-to-one; markup and annotation)

Operations in TAG are operations on sets of nodes and edges

____

# TAG in 3D (Video is preferred here)

<img class="three-d" src="../Balisage-1-3-xsl/3d_new_perspective.png"/>

____

# Overlap (multiple hierarchies) in TAG

Percy Bysshe Shelley, “Ozymandias”

> Who said — **“Two vast and trunkless lets of stone  
Stand in the desart....** Near them, on the sand

<img src="../Balisage-1-3-xsl/ozymandias_hypergraph_transparent.png" width="99%"/>

<!-- ai the hierarchies are not really all that visible here, since the "dominate" relation is not used. Say something here about the difference between containment and dominance? -->

____

# Discontinuity in TAG

<img src="../Balisage-1-3-xsl/discontinuity_hypergraph_transparent.png" width="99%"/>

____
# Textual phenomena II

* White space as crypto-overlap
* Datatyping and artificial hierarchy
* Footnotes (Scope of reference)

# White space as crypto-overlap

Percy Bysshe Shelley, “Ozymandias”

> Who said two vast and trunkless legs of stone
 
```xml
<line>
	<foot>Who said</foot>
	<foot>two vast</foot>
	<foot>and trunk</foot><foot>less legs</foot>
	<foot>of stone</foot>
</line>
```
The following pseudo-XML is not well formed:

```xml
<foot><word>and</word> <word>trunk</foot><foot>less</word> <word>legs</word></foot>
```