<style style="display: none;" type="text/css">
    ol > li > ol { list-style-type: lower-alpha; }
</style>
# Outline

(Not yet integrated into XML file; David will do that.)

1. Where we are today: The XML tree model has several well-known limitations, some of which have received a lot of attention (overlap) and some of which have not (discontinuity; white space as crypto-overlap). All of these have well-known work-arounds that have disadvantages, but because they work and because XML has a large user community, it is difficult to overcome inertia and move to a technology that does not require awkward work-arounds.
1. Requirements for an ideal (or, at least, improved) text model (focus on features not well supported by XML [tree] modeling)
	1. The goal is to add layers and layers of extra information to the text. These layers can be created by a human (manually) or added by a computer using parsers. Or a mix of both.
	1. These layers can overlap each other or be discontinuous.
	1. Possibility to read as well as write.
	1. Possibility to defer decisions about relations between layers. I.e., a hierarchy can be applied later, just like a schema is used right now in XML to validate a document.
1. Introduce the TAG/hypergraph model for text as a processing model for the text and all layers of annotations. Illustrate general functionality, without emphasis on overlap, discontinuity, or white space, which are in focus below.
1. How TAG addresses structures that are awkward for XML (description, XML approach, TAG approach, examples)
	1. Overlap. Examples include enjambment in poetry, pages/paragraphs in prose, Frankenstein.
	1. White space as crypto-overlap. Examples include caesura in poetry.
	1. Discontinuity. Examples include divided or interrupted speech in prose.
1. Compare and contrast TAG/hypergraph with previous models for text processing, such as DOM, GODDAG, LMNL data model (ranges)
	1. TAG and DOM
	1. TAG and GODDAG 
	1. TAG and LMNL
	    1. The LMNL and TAG data models
	    1. LMNL syntax in a TAG environment
	    1. What LMNL syntax doesn't represent (apparently reserved for the limen, and not yet specified) that TAG requires
1. TAG in Alexandria (some of which may be plans or projections, rather than implementation)
	1. Introduction to Alexandria as a TAG implementation
	1. Graph and hypergraph
	1. Navigation and query
	1. Import and export
