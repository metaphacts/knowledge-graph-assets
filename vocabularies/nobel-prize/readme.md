# Nobel Prize Vocabulary

[This SKOS vocabulary](nobel-prize-metaphacts-skos-vocabulary.ttl) was created by [metaphacts GmbH](http://metaphacts.com/) for demonstration purpose only. 

While the official [nobel prize specification page](https://data.nobelprize.org/specification/) (version from June 2021) talks about "vocabularies", the [official OWL ontology](http://data.nobelprize.org/terms.rdf) defines only implicitly the category terms as instances of SKOS concept without publishing them as a dedicated SKOS vocabulary scheme. 

To handle the vocabulary terms within [metaphactory](https://metaphacts.com/product), the identifiers of the "category" individuals from the [official OWL ontology](http://data.nobelprize.org/terms.rdf) have been reused and turned into an explicitly vocabulary (defined as SKOS scheme). Additionally, the terms have been augmented and enriched with additional structure and metadata solely for exploration and demonstration purpose.

Please note:
* This **IS NOT** an official artefact (it is not authored, reviewed, curated or published by the official nobel prize website) and it **IS NOT** reflecting the official nobel prize categories (see changes below). This repository and metaphacts are not associated to the nobel prize organization and website in any way.
* As of July 2022, there are known inconsistencies between the [official data](https://data.nobelprize.org/sparql) and the [official OWL ontology](http://data.nobelprize.org/terms.rdf). The inconsistencies were found with help of the metaphacts’ [SHACL version of the ontology](https://github.com/metaphacts/knowledge-graph-assets/blob/master/ontologies/nobel-prize/nobel-prize-metaphacts-shacl-ontology.ttl) and the following adaptations have been made by metaphacts within this vocabulary:
  * `<http://data.nobelprize.org/terms/Litterature>` as used by the [official OWL ontology](http://data.nobelprize.org/terms.rdf) was renamed to `<http://data.nobelprize.org/terms/Literature>` to match the [official instance data](https://data.nobelprize.org/sparql)
  * `<http://data.nobelprize.org/terms/Physiology_or_Medicin>` as used by the [official OWL ontology](http://data.nobelprize.org/terms.rdf) was renamed to `<http://data.nobelprize.org/terms/Physiology_or_Medicine>`  to match the [official instance data](https://data.nobelprize.org/sparql) 
  * The [official instance data](https://data.nobelprize.org/sparql) uses a mix of namespaces (e.g. `http://data.nobelprize.org/terms/Physics` vs `http://data.nobelprize.org/resource/category/Physics`). Since the [official OWL ontology](http://data.nobelprize.org/terms.rdf) uses `http://data.nobelprize.org/terms/`, this vocabulary uses the same namespaces.
    ```
    SELECT DISTINCT ?g (count(*) as ?cnt) {
    ?s <http://data.nobelprize.org/terms/category> ?g
    }GROUP BY ?g
    ------results----
    "http://data.nobelprize.org/resource/category/Chemistry","188"
    "http://data.nobelprize.org/resource/category/Economic_Sciences","89"
    "http://data.nobelprize.org/resource/category/Literature","117"
    "http://data.nobelprize.org/resource/category/Peace","137"
    "http://data.nobelprize.org/resource/category/Physics","219"
    "http://data.nobelprize.org/resource/category/Physiology_or_Medicine","224"
    "http://data.nobelprize.org/terms/Chemistry","113"
    "http://data.nobelprize.org/terms/Economic_Sciences","53"
    "http://data.nobelprize.org/terms/Literature","113"
    "http://data.nobelprize.org/terms/Peace","102"
    "http://data.nobelprize.org/terms/Physics","115"
    "http://data.nobelprize.org/terms/Physiology_or_Medicine","112"
 * All extensions (IRIs which do not appear in the official data or ontology) using the namespace `http://data.nobelprize.org/terms-ext/`. 
   * Particularly, `http://data.nobelprize.org/terms-ext/Categories` and `http://data.nobelprize.org/terms-ext/Science-of-Nature` have been introduced as additional `skos:Concept` to augmented the existing terms with additional structure. Both **are not** official nobel prize category terms.
 * This vocabulary run out of synch or only be asynchronously updated as data is published or updated by the nobel prize website (c.f. https://data.nobelprize.org/sparql).