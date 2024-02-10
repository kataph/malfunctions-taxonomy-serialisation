# MALFO serialization
This repo contains various serializations of the ontology MALFO (MALFunction Ontology): 
- first-order logic: MALFO is serialized in the languages clif (Common Logic Interchange Format), tptp (Thousands of Problems for Theorem Provers format), and p9 (Prover9). The clif version was parsed with The .clif axioms were parsed with macleod: https://github.com/thahmann/macleod. With the same tool the tptp and p9 version were generated automatically.
- disjuntive datalog: MALFO is serialized in a disjunctive datalog  language (MALFO.pl has been parsed with [DLV](https://www.dlvsystem.it/dlvsite/dlv/)). Note that MALFO.pl contains a program roughly equivalent to first-order MALFO (the signature of DLV MALFO has been expanded with auxiliary predicates to realize the equivalence: these should be removed if used in applications, especially those participating in existential rules, otherwise there is the risk of slow or non-terminating program executions).
- OWL: a manually-curated reduction of first-order MALFO to OWL is present in MALFO.owl. Testing of reasoning happened on Protegé 5.5.0, with Hermit 1.4.3.456: note that bugs with reasoning tasks were found using more recent version of Protegé. Moreover, note that an ad-hoc reasoning system has been implemented, bypassing the need for (complete but cumbersome) OWL reasoning. The ad-hoc reasoning is implemented through queries, so that its application to, say, a graph on a triplestore would be convenient. To execute such reasoning, run `infer.py' and input the name of any file containing an instantiation of MALFO OWL ontology. A corresponding output file with the inferences materialized will be created. Domain and range axioms will also be checked.  

Consistency of the first-order theory has been confirmed using Vampire through the "Systems on TpTp" tool available at: https://www.tptp.org/cgi-bin/SystemOnTPTP, while the OWL theory has been applied to some models.

## MALFO models 
The models have been encoded in graphml files for the sake of visual presentation. A script, `read_graphml.py' is supplied that converts these into knowledge graphs. The script assumes that the input files have the xml structure of documents generated by the [yEd desktop app](https://www.yworks.com/products/yed) and follow the same convention in terms of mapping shapes, colors, and edge labels to MALFO OWL terms. In particular, is not intended to replace an ontology editor. To convert a graphml file, simply run the script and input the name or path of the graphml file. A corresponding output file will be created. 
