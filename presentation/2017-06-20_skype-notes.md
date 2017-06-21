# Notes from Skype conversation, 2017-06-20 djb rhd

## Two types of limitations of the XML model

The limitations of the XML model affect the capabilities of XML processing in at least two ways. The first involves *model*; the second involves *lexicon*. TAG addresses the first, but not the second. Both arise especially in heterogeneous corpora, that is, situations where documents that must be federated may not have been tagged in entirely the same way.

### The modeling challenge

The modeling challenge is that work-arounds for XML limitations vary. For example, to tag both sentences and lines in verse, either one may be expressed with container tags, but not both, so the other is typically represented by milestones. The reason this is a modeling challenge is that a heterogeneous corpus may include some documents that resolve it in one way and some in the other. By eliminating “the overlap problem” at the level of the model, TAG obviates the need for a workaround and makes it possible to represent such structures in a unified way. The same is true with respect to discontinuity. In XML, stitching together the parts of a divided quotation requires information about markup semantics, while TAG resolves discontinuity at the level of the model. The same is true about whitespace tokenization of tagged text. 

In XML this type of issue is expressed *syntactically*, since XML is a markup language defined by its syntax, but it's fundamentally a modeling issue, since the syntax is imposed by the tree model.

The modeling challenge also has engineering consequences. Insofar as XML represents a tree, modeling that is consistent with the tree permits operations on the tree, and tree traversal is efficient. Workarounds that do not express the tree structure (e.g., Trojan milestones, join-pointer attributes) necessitate traversal not based on the tree, that is, suboptimal traversal. This is why traversing the long horizontal XPath axes (preceding::, following::) is typically less efficient than other XPath traversal. (See https://www.balisage.net/Proceedings/vol3/html/Birnbaum01/BalisageVol3-Birnbaum01.html.)

### The lexical challenge 

The lexical challenge affects TAG and XML comparably: different documents may use different Markup node `name` properties (TAG) or generic identifiers (XML) with the same meaning, e.g., “s” or “sentence” for a sentence. The TEI addresses this with guidelines, which are invitations to a common vocabulary, although that purpose is compromised in situations where the TEI provides alternative ways of doing the same thing. DITA addresses it with a standard. This matter is inherently semantic, and therefore requires access to markup semantics in both XML and TAG.
