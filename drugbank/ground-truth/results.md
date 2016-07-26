
This is mostly the results and discussion on the drugbank dataset (and a set of issues to improve the results) than a stand-alone issue.

To reproduce the results run the following command
```bash
xcurator.bat -f xcurator-data/drugbank/data/drugbank-sample-sm.xml -m xcurator-data/drugbank/data/mapping-sm.xml -s U
``` 
The `drugbank-sample-sm.xml` has 96 drug entities. This experiment only uses the basic entity discovery (implemented in [`BasicEntityDiscovery`](https://github.com/xcurator/xcurator/blob/ver2/src/edu/toronto/cs/xcurator/discoverer/BasicEntityDiscovery.java) class). 

## Results
The extracted entities and attributes and accuracy of the discoverer given in this section. 
### Entities
The discovered entities as well as the entities in the drugbank ground-truth and their intersection are given in the following: 

#### Discovered entities:
`  [snp-adverse-drug-reactions, calculated-properties, drug-interaction, go-classifier, mixtures, drug, external-links, pfam, price, property, food-interactions, external-identifier, drugbank, polypeptide, organism, level, synonyms, international-brand, pathways, carriers, snp-effects, classification, packager, sequence, atc-code, effect, actions, go-classifiers, external-link, affected-organisms, dosage, right-element, experimental-properties, external-identifiers, patent, transporters, dosages, enzymes, pfams, sequences, targets, manufacturer, products, synonym, mixture, atc-codes, patents, categories, prices, left-element, salts, enzyme, product, reaction, cost, salt, manufacturers, drug-interactions, drugs, groups, packagers, target, international-brands, amino-acid-sequence, carrier, transporter, pathway, reactions, ahfs-codes, category, gene-sequence, drugbank-id]
`
> size: 72


#### Entities in ground-truth:
`
 [toxicity, substructures, pharmaceutical, inchikey, smiles, molecular-weight, source, type, drug, refractivity, polar-surface-area-(psa), pharmacology, food-interaction, brand, logs, logp, group, boiling-point, polarizability, mechanism-of-action, inchi, absorption, caco2-permeability, monoisotopic-weight, rule-of-five, ghose-filter, water-solubility, half-life, unit, molecular-formula, volume-of-distribution, route-of-elimination, bioavailability, pka-(strongest-basic), transporter-relation, physiological-charge, indication, patent, rotatable-bond-count, pka, mddr-like-rule, traditional-iupac-name, manufacturer, protein-binding, iupac-name, synonym, isoelectric-point, drug-drug-interaction, mixture, number-of-rings, clearance, h-bond-donor-count, carrier-relation, enzyme, salt, h-bond-acceptor-count, kingdom, target, affected-organism, enzyme-relation, biotransformation, hydrophobicity, carrier, pka-(strongest-acidic), transporter, melting-point, category, target-relation]
`
> size: 68


#### Intersection:
`
 [drug, patent, manufacturer, synonym, mixture, enzyme, salt, target, carrier, transporter, category]
`
> size: 11


#### Entities statistics:
```
Prec:	0.1528
Recall:	0.1618
F1:	0.1571
```


### Attributes
The results for attributes are given in the following: 


#### Discovered attributes:
`
 [references, pharmacodynamics, cas-number, type, mixtures, gene-name, number, approved, superclass, external-links, ndc-id, action, id, mesh-id, identifier, synthesis-reference, mechanism-of-action, absorption, synonyms, fda-application-number, snp-effects, carriers, route, volume-of-distribution, indication, go-classifiers, actions, primary, theoretical-pi, pubmed-id, dosages, general-function, enzymes, pfams, sequences, targets, dpd-id, products, inhibition-strength, ingredients, clearance, currency, categories, rs-id, substituent, cellular-location, chromosome-location, salts, url, packagers, direct-parent, subclass, transmembrane-regions, reactions, ahfs-codes, drugbank-id, toxicity, country, snp-adverse-drug-reactions, general-references, coder, inchikey, protein-name, strength, molecular-weight, language, source, ndc-product-code, specific-function, known-action, food-interactions, food-interaction, gene-symbol, defining-change, group, organism, resource, ncbi-taxonomy-id, created, kind, format, pathways, half-life, adverse-reaction, sequence, unit, route-of-elimination, uniprot-id, name, metabolism, position, updated, affected-organisms, over-the-counter, expires, experimental-properties, code, transporters, description, protein-binding, smpdb-id, synonym, induction-strength, atc-codes, patents, company, prices, value, class, manufacturers, drug-interactions, started-marketing-on, ended-marketing-on, ahfs-code, kingdom, generic, international-brands, affected-organism, form, alternative-parent, allele, dosage-form, signal-regions, locus, category]
`
> size: 125


#### Attributes in ground-truth:
`
 [toxicity, country, x-ahfs, molecular-weight, calculated-properties, x-chebi, x-atc, source, type, drug, gene-name, reference, x-uniprot, approved, known-action, specific-function, price, pharmacology, action, x-bindingdb, id, food-interaction, brand, x-iuphar, x-kegg, group, organism, mechanism-of-action, absorption, x-pdb, x-ndc, x-wikipedia, half-life, packager, x-pharmgkb, x-pubchemsubstance, route, x-dpd, volume-of-distribution, route-of-elimination, name, x-genecards, indication, substructure, dosage, expires, experimental-properties, theoretical-pi, patent, x-chemspider, general-function, manufacturer, protein-binding, synonym, mixture, x-genatlas, x-genbank, ingredients, x-hgnc, clearance, value, cellular-location, enzyme, x-gi, ddi-interactor-in, product, ingredient, salt, x-pubchemcompound, kingdom, target, affected-organism, biotransformation, carrier, form, transporter, transmembrane-regions, locus, category, x-gtp]
`
> size: 80

#### Intersection:
`
 [type, gene-name, approved, action, id, mechanism-of-action, absorption, route, volume-of-distribution, indication, theoretical-pi, general-function, ingredients, clearance, cellular-location, transmembrane-regions, toxicity, country, molecular-weight, source, specific-function, known-action, food-interaction, group, organism, half-life, route-of-elimination, name, expires, experimental-properties, protein-binding, synonym, value, kingdom, affected-organism, form, locus, category]
`
> size: 38


#### Attributes statistics:
```
Prec:	0.304
Recall:	0.475
F1:	0.3707
```

### Missing/Extra entities and attributes
There are some entities that are in the ground-truth and the discoverer didn't recognize them not in the entities neither in the attributes. Also, it recognized some extra entities and attributes that might use to improve the ground-truth's quality.
 
#### Entity and attributes that seen only in the ground-truth:
`
[substructures, x-ahfs, smiles, x-chebi, x-atc, refractivity, brand, boiling-point, caco2-permeability, x-ndc, monoisotopic-weight, ghose-filter, x-pubchemsubstance, x-dpd, physiological-charge, x-genecards, substructure, x-chemspider, rotatable-bond-count, mddr-like-rule, isoelectric-point, x-hgnc, h-bond-donor-count, carrier-relation, x-gi, ingredient, x-pubchemcompound, enzyme-relation, biotransformation, target-relation, pharmaceutical, reference, x-uniprot, polar-surface-area-(psa), pharmacology, x-bindingdb, logs, x-iuphar, logp, x-kegg, polarizability, inchi, x-pdb, rule-of-five, x-wikipedia, water-solubility, x-pharmgkb, molecular-formula, bioavailability, pka-(strongest-basic), transporter-relation, pka, traditional-iupac-name, iupac-name, drug-drug-interaction, x-genatlas, number-of-rings, x-genbank, ddi-interactor-in, h-bond-acceptor-count, hydrophobicity, pka-(strongest-acidic), melting-point, x-gtp]
`
> size: 64
 
#### Entity and attributes that seen only in the results:
`
[references, pharmacodynamics, go-classifier, cas-number, mixtures, number, external-links, superclass, property, ndc-id, mesh-id, drugbank, identifier, synthesis-reference, synonyms, fda-application-number, carriers, snp-effects, classification, atc-code, actions, go-classifiers, primary, pubmed-id, dosages, enzymes, pfams, sequences, targets, dpd-id, products, inhibition-strength, currency, categories, rs-id, substituent, salts, chromosome-location, reaction, drugs, packagers, url, direct-parent, subclass, pathway, reactions, ahfs-codes, drugbank-id, snp-adverse-drug-reactions, general-references, coder, protein-name, strength, language, ndc-product-code, drug-interaction, pfam, food-interactions, gene-symbol, defining-change, external-identifier, polypeptide, level, resource, ncbi-taxonomy-id, created, kind, format, international-brand, pathways, adverse-reaction, sequence, uniprot-id, effect, metabolism, position, external-link, updated, affected-organisms, over-the-counter, right-element, external-identifiers, code, transporters, description, smpdb-id, induction-strength, atc-codes, patents, company, prices, class, left-element, cost, manufacturers, drug-interactions, started-marketing-on, groups, ended-marketing-on, ahfs-code, generic, international-brands, amino-acid-sequence, alternative-parent, allele, dosage-form, signal-regions, gene-sequence]
`
> size: 108

### Entity and Attribute misplacements
The entities and attributes that the discoverer recognizes wrongly (attribute as entity and vice versa).

#### Attributes that recognized as entity:
`
[calculated-properties, drug, price, organism, packager, dosage, experimental-properties, patent, manufacturer, synonym, mixture, enzyme, product, salt, target, carrier, transporter, category]
`
> size: 18

#### Entities that recognized as attribute:
`
[toxicity, inchikey, molecular-weight, source, type, food-interaction, group, mechanism-of-action, absorption, half-life, unit, volume-of-distribution, route-of-elimination, indication, protein-binding, synonym, clearance, kingdom, affected-organism, category]
`
> size: 20

## Discussion
- Most of the entities that we recognized but they are not in the ground-truth are grouping nodes (e.g. `snp-adverse-drug-reactions`, `calculated-properties`, `drug-interaction`, `go-classifier`, ...). By removing these entities, we will get improvment on the results. It should be noted, we recognized these elements as both entity and attribute, so it will effect on both sides. 
- We missed all entities that recognized as `calculated-properties` in the ground-truth. These entities are values for property tags, since we didn't apply flatting step, we missed them. For example in the following, `logp`, `logs` and `water-solubility` are entities.  
```
<calculated-properties>
	<property>
		<kind>logP</kind>
		<value>0.3</value>
		<source>ALOGPS</source>
	</property>
	<property>
		<kind>logS</kind>
		<value>-4.7</value>
		<source>ALOGPS</source>
	</property>
	<property>
		<kind>Water Solubility</kind>
		<value>2.83e-02 g/l</value>
		<source>ALOGPS</source>
	</property>
...
</calculated-properties>
```

- Some of the elements are actual element in the ground-truth, but in the OWL file, they considered it as entity, for example 'half-life' that is a simple free-text string but in the schema it's an entity.

## Appendix
### Drugbank Ground Truth

We obtained the ground-truth for Dragbank dataset from bio2rdf project. [[OWL File]](http://download.bio2rdf.org/release/3/drugbank/drugbank.schema.owl)
For extracting the entities and attributes, we used the following SPARQL query:

```sparql
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX b2r: <http://bio2rdf.org/>
PREFIX dcterms: <http://purl.org/dc/terms/>

SELECT  distinct ?t ?c
WHERE { 
?s rdf:type ?c .
?s dcterms:title ?t
} order by ?c
```

The entities are `owl:Class` elements and the attributes are union of `owl:DatatypeProperty` and `owl:ObjectProperty` elements. 
For exploring the owl files we are using [Protege](http://protege.stanford.edu/) editor.
 

