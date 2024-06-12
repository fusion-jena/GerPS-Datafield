# Competence questions

# 1. CQ
Welche Stammdatenschematas gibt es?  

```sparql
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xdf: <https://w3id.org/GerPS-onto/FIMDatenfelder#>
SELECT *
WHERE {	
	?Stammdatenschematas a xdf:J000002 .
}
```

[Antwort](./cq1.csv)

# 2. CQ
Welche Datenfelder und Datenfeldgruppen enthält ein Stammschemata?

```SPARQL
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xdf: <https://w3id.org/GerPS-onto/FIMDatenfelder#>
SELECT ?Element
WHERE {	
  <https://test.schema-repository.fitko.dev/schema/baukasten/S00000094/1.0> (xdf:JP000010/xdf:JP000011)+  ?Element .
}
```

[Antwort](./cq2.csv)

# 3. CQ
Welche Datenfelder und Datenfeldgruppen enthält eine Datenfeldgrupp?

```sparql
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xdf: <https://w3id.org/GerPS-onto/FIMDatenfelder#>
SELECT *
WHERE {	
	<https://test.schema-repository.fitko.dev/groups/baukasten/G00000253/1.0> (xdf:JP000010/xdf:JP000011)+ ?Elemente .
} 
```

[Antwort](./cq3.csv)


# 4. CQ
Welche Regeln enthält ein Datenfelder oder eine Datenfeldgruppen?

```sparql
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xdf: <https://w3id.org/GerPS-onto/FIMDatenfelder#>
SELECT *
WHERE {	
	<https://test.schema-repository.fitko.dev/groups/baukasten/G00001399/1.0> xdf:JP000005 ?Regeln .
} 
```

[Antwort](./cq4.csv)


# 5. CQ
Welche Regeln enthält ein Stammdatenschemata?

```sparql
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xdf: <https://w3id.org/GerPS-onto/FIMDatenfelder#>

SELECT ?Regeln
WHERE {	
	<https://test.schema-repository.fitko.dev/schema/baukasten/S00000094/1.0> (xdf:JP000010/xdf:JP000011)+ ?element .
  	?element xdf:JP000005 ?Regeln .
}
```

[Antwort](./cq5.csv)


# 6. CQ
Auf welchen Handlungsgrundlagen beruht ein Stammdatenschemata/Datenfeld/Datenfeldgruppe/(opt.) Regel?

```sparql
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xdf: <https://w3id.org/GerPS-onto/FIMDatenfelder#>

SELECT ?Element ?Grundlage
WHERE {	
	?Element <https://w3id.org/GerPS-onto/ontology#basiert_auf> ?basis .
  	?basis rdfs:label ?Grundlage
}
```

[Antwort](./cq6.csv)


# 7. CQ
Wer ist der Verfasser des Stammdatenschamatas?

```sparql
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xdf: <https://w3id.org/GerPS-onto/FIMDatenfelder#>

SELECT ?author
WHERE {	
	<https://test.schema-repository.fitko.dev/schema/baukasten/S00000094/1.0> xdf:JD000014 ?author .
}
``` 

[Antwort](./cq7.csv)


# 8. CQ
Welche Datenfelder/Datenfeldgruppen stehen in der ersten Ebene eines Stammdatenschematas?

```sparql
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX eupont: <http://elite.polito.it/ontologies/eupont.owl#>
PREFIX xdf: <https://w3id.org/GerPS-onto/FIMDatenfelder#>

Select ?Stammdatenschema ?Element 
WHERE {
    ?Stammdatenschema a xdf:J000002 .
   	?Stammdatenschema xdf:JP000010/xdf:JP000011 ?Element
} 
``` 

[Antwort](./cq8.csv)


# 9. CQ
Gibt es in der ersten Ebene eines Stammdatenschematas eine Datenfelder/Datenfeldgruppen die auch in anderen Stammdateschematas vorkommen?

```sparql
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX eupont: <http://elite.polito.it/ontologies/eupont.owl#>
PREFIX xdf: <https://w3id.org/GerPS-onto/FIMDatenfelder#>

Select ?element 
WHERE {
    ?sub a xdf:J000002 .
   	?sub xdf:JP000010/xdf:JP000011 ?element . 
  
  	?sub2 a xdf:J000002 .
    ?sub2 xdf:JP000010/xdf:JP000011 ?element .
  	FILTER(?sub != ?sub2)
} 
``` 

[Antwort](./cq9.csv)


# 10. CQ
Welche Bedingungen hat eine Regel?

```sparql
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX eupont: <http://elite.polito.it/ontologies/eupont.owl#>
PREFIX df: <https://w3id.org/GerPS-onto/FIMDatenfelder#>

Construct{
  ?condition 		a 				?class1 .
  
  ?condition		eupont:value	?value3 . 
  ?condition		df:JP000006	?Field3.
  
  ?condition 		df:JP000002		?leftCondition .
  ?condition 		df:JP000003		?rightCondition .
  

  ?leftCondition 	  a 				?class2 .
  ?rightCondition 	a 				?class3 .
  
  ?rightCondition 	df:JP000006 ?Field1 .
  ?leftCondition 	  df:JP000006 ?Field2 .
    
  ?rightCondition 	eupont:value ?value1 .
  ?leftCondition 	eupont:value ?value2 .
}
WHERE {
  {
    ?condition 		df:JP000007 	<https://test.schema-repository.fitko.dev/rules/baukasten/R00000042/1.0> 	.
    ?condition 			a 				?class1 .
    FILTER(?class1 != owl:NamedIndividual) .
    

      ?leftCondition 		df:JP000007   <https://test.schema-repository.fitko.dev/rules/baukasten/R00000042/1.0> 	.
      ?rightCondition 	df:JP000007 	<https://test.schema-repository.fitko.dev/rules/baukasten/R00000042/1.0>	.
    
      ?condition 			df:JP000002		?leftCondition .
      ?condition 			df:JP000003		?rightCondition . 
      
      ?leftCondition 		a 				?class2 .
      ?rightCondition 	a 				?class3 .  
      
      FILTER(?class2 != owl:NamedIndividual) .
      FILTER(?class3 != owl:NamedIndividual) .
      FILTER(?class2 != <http://elite.polito.it/ontologies/eupont.owl#RuleAxiom>) .
      FILTER(?class3 != <http://elite.polito.it/ontologies/eupont.owl#RuleAxiom>) .
      FILTER(?class2 != <http://elite.polito.it/ontologies/eupont.owl#RuleNominalAxiom>) .
      FILTER(?class3 != <http://elite.polito.it/ontologies/eupont.owl#RuleNominalAxiom>) .
      Filter(?class3 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000009>) .
      Filter(?class3 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000018>) .
      Filter(?class3 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000021>) .
      Filter(?class2 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000009>) .
      Filter(?class2 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000018>) .
      Filter(?class2 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000021>) .

    OPTIONAL{
      ?rightCondition 	df:JP000006 	?Field1 .   
      ?rightCOndition 	eupont:value 			?value1 .
    }
    
    OPTIONAL{
      ?leftCondition 		df:JP000006	?Field2 .
      ?leftCondition 		eupont:value 			?value2 .
    }
    
    OPTIONAL{
      ?condition 			df:JP000006 	?Field3 .   
      ?condition 			eupont:value 			?value3 .
    }
  }
  UNION{
  	?condition 		df:JP000007 	<https://test.schema-repository.fitko.dev/rules/baukasten/R00000042/1.0>	.
    ?condition 			a 				?class1 .
    FILTER(?class1 != <http://elite.polito.it/ontologies/eupont.owl#RuleAxiom>) .
    FILTER(?class1 != <http://elite.polito.it/ontologies/eupont.owl#RuleNominalAxiom>) .
    Filter(?class1 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000009>) .
    Filter(?class1 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000018>) .
    Filter(?class1 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000021>) .
    FILTER(?class1 != owl:NamedIndividual) .

      ?condition 			df:JP000006 	?Field3 .   
      ?condition 			eupont:value 			?value3 .
 
  }
} 
```

[Antwort](./cq10.ttl)


# 11. CQ
In welchen Beziehungen stehen die Bedingungen einer Regel zueinander?

```sparql
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX eupont: <http://elite.polito.it/ontologies/eupont.owl#>
PREFIX df: <https://w3id.org/GerPS-onto/FIMDatenfelder#>

Construct{
  ?condition 		a 				?class1 .
  
  ?condition		eupont:value	?value3 . 
  ?condition		df:JP000006	?Field3.
  
  ?condition 		df:JP000002		?leftCondition .
  ?condition 		df:JP000003		?rightCondition .
  

  ?leftCondition 	  a 				?class2 .
  ?rightCondition 	a 				?class3 .
  
  ?rightCondition 	df:JP000006 ?Field1 .
  ?leftCondition 	  df:JP000006 ?Field2 .
    
  ?rightCondition 	eupont:value ?value1 .
  ?leftCondition 	eupont:value ?value2 .
}
WHERE {
  {
    ?condition 		df:JP000007 	<https://test.schema-repository.fitko.dev/rules/baukasten/R00000042/1.0> 	.
    ?condition 			a 				?class1 .
    FILTER(?class1 != owl:NamedIndividual) .
    

      ?leftCondition 		df:JP000007   <https://test.schema-repository.fitko.dev/rules/baukasten/R00000042/1.0> 	.
      ?rightCondition 	df:JP000007 	<https://test.schema-repository.fitko.dev/rules/baukasten/R00000042/1.0>	.
    
      ?condition 			df:JP000002		?leftCondition .
      ?condition 			df:JP000003		?rightCondition . 
      
      ?leftCondition 		a 				?class2 .
      ?rightCondition 	a 				?class3 .  
      
      FILTER(?class2 != owl:NamedIndividual) .
      FILTER(?class3 != owl:NamedIndividual) .
      FILTER(?class2 != <http://elite.polito.it/ontologies/eupont.owl#RuleAxiom>) .
      FILTER(?class3 != <http://elite.polito.it/ontologies/eupont.owl#RuleAxiom>) .
      FILTER(?class2 != <http://elite.polito.it/ontologies/eupont.owl#RuleNominalAxiom>) .
      FILTER(?class3 != <http://elite.polito.it/ontologies/eupont.owl#RuleNominalAxiom>) .
      Filter(?class3 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000009>) .
      Filter(?class3 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000018>) .
      Filter(?class3 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000021>) .
      Filter(?class2 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000009>) .
      Filter(?class2 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000018>) .
      Filter(?class2 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000021>) .

    OPTIONAL{
      ?rightCondition 	df:JP000006 	?Field1 .   
      ?rightCOndition 	eupont:value 			?value1 .
    }
    
    OPTIONAL{
      ?leftCondition 		df:JP000006	?Field2 .
      ?leftCondition 		eupont:value 			?value2 .
    }
    
    OPTIONAL{
      ?condition 			df:JP000006 	?Field3 .   
      ?condition 			eupont:value 			?value3 .
    }
  }
  UNION{
  	?condition 		df:JP000007 	<https://test.schema-repository.fitko.dev/rules/baukasten/R00000042/1.0>	.
    ?condition 			a 				?class1 .
    FILTER(?class1 != <http://elite.polito.it/ontologies/eupont.owl#RuleAxiom>) .
    FILTER(?class1 != <http://elite.polito.it/ontologies/eupont.owl#RuleNominalAxiom>) .
    Filter(?class1 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000009>) .
    Filter(?class1 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000018>) .
    Filter(?class1 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000021>) .
    FILTER(?class1 != owl:NamedIndividual) .

      ?condition 			df:JP000006 	?Field3 .   
      ?condition 			eupont:value 			?value3 .
 
  }
} 
```

[Antwort](./cq11.ttl)


# 12. CQ
Welche Aktionen hat eine Regel?

```sparql
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX eupont: <http://elite.polito.it/ontologies/eupont.owl#>
PREFIX df: <https://w3id.org/GerPS-onto/FIMDatenfelder#>

Construct{
  ?Action1 df:JP000004 ?Action2 .
  ?Action1 a ?class1 .
  ?Action2 a ?class2 .
  ?Action1 df:JP000008 ?target.
}
WHERE {
    ?Action1 df:JP000007 	<https://test.schema-repository.fitko.dev/rules/baukasten/R00000042/1.0> .
	  ?Action1 df:JP000008 ?target.
    ?Action1 a ?class1 .
    FILTER(?class1 != owl:NamedIndividual) .
    FILTER(?class1 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000011>) .
    FILTER(?class1 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000008>) .
    FILTER(?class1 != <http://elite.polito.it/ontologies/eupont.owl#RuleAxiom>) .
    FILTER(?class1 != <http://elite.polito.it/ontologies/eupont.owl#RuleNominalAxiom>) .
    FILTER(?class1 != <http://elite.polito.it/ontologies/eupont.owl#Action>) .
  
    OPTIONAL{
      ?Action1 df:JP000004	?Action2.
      ?Action2 df:JP000007 	<https://test.schema-repository.fitko.dev/rules/baukasten/R00000042/1.0> .
      ?Action2 a ?class2 .
      FILTER(?class2 != owl:NamedIndividual) .
      FILTER(?class2 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000011>) .
      FILTER(?class2 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000008>) .
      FILTER(?class2 != <http://elite.polito.it/ontologies/eupont.owl#RuleAxiom>) .
      FILTER(?class2 != <http://elite.polito.it/ontologies/eupont.owl#RuleNominalAxiom>) .
      FILTER(?class2 != <http://elite.polito.it/ontologies/eupont.owl#Action>) .
    }
} 
```

[Antwort](./cq12.ttl)


# 13. CQ
In welcher Reihenfolge stehen die Aktionen einer Regel?

```sparql
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX eupont: <http://elite.polito.it/ontologies/eupont.owl#>
PREFIX df: <https://w3id.org/GerPS-onto/FIMDatenfelder#>

Construct{
  ?Action1 df:JP000004 ?Action2 .
  ?Action1 a ?class1 .
  ?Action2 a ?class2 .
  ?Action1 df:JP000008 ?target.
}
WHERE {
    ?Action1 df:JP000007 	<https://test.schema-repository.fitko.dev/rules/baukasten/R00000042/1.0> .
	  ?Action1 df:JP000008 ?target.
    ?Action1 a ?class1 .
    FILTER(?class1 != owl:NamedIndividual) .
    FILTER(?class1 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000011>) .
    FILTER(?class1 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000008>) .
    FILTER(?class1 != <http://elite.polito.it/ontologies/eupont.owl#RuleAxiom>) .
    FILTER(?class1 != <http://elite.polito.it/ontologies/eupont.owl#RuleNominalAxiom>) .
    FILTER(?class1 != <http://elite.polito.it/ontologies/eupont.owl#Action>) .
  
    OPTIONAL{
      ?Action1 df:JP000004	?Action2.
      ?Action2 df:JP000007 	<https://test.schema-repository.fitko.dev/rules/baukasten/R00000042/1.0> .
      ?Action2 a ?class2 .
      FILTER(?class2 != owl:NamedIndividual) .
      FILTER(?class2 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000011>) .
      FILTER(?class2 != <https://w3id.org/GerPS-onto/FIMDatenfelder#J000008>) .
      FILTER(?class2 != <http://elite.polito.it/ontologies/eupont.owl#RuleAxiom>) .
      FILTER(?class2 != <http://elite.polito.it/ontologies/eupont.owl#RuleNominalAxiom>) .
      FILTER(?class2 != <http://elite.polito.it/ontologies/eupont.owl#Action>) .
    }
} 
```

[Antwort](./cq13.ttl)


# 14. CQ
Welche Datenfelder/Datenfeldgruppen stehen mit einer bestimmten Regel in Verbindung?

```sparql
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX eupont: <http://elite.polito.it/ontologies/eupont.owl#>
PREFIX xdf: <https://w3id.org/GerPS-onto/FIMDatenfelder#>

Select ?element 
WHERE {
    ?sub xdf:JP000007 <https://test.schema-repository.fitko.dev/rules/baukasten/R00000042/1.0> .
    ?sub xdf:JP000008|xdf:JP000006 ?element .
} 
```

[Antwort](./cq14.csv)


# 15. CQ
Welche Datenfelder/Datenfeldgruppen stehen mit der Bedinengung einer bestimmten Regel in Verbindung?  

```sparql
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX eupont: <http://elite.polito.it/ontologies/eupont.owl#>
PREFIX xdf: <https://w3id.org/GerPS-onto/FIMDatenfelder#>

Select ?element 
WHERE {
    ?sub xdf:JP000007 <https://test.schema-repository.fitko.dev/rules/baukasten/R00000042/1.0> .
    ?sub xdf:JP000006 ?element .
} 
```

[Antwort](./cq15.csv)


# 16. CQ
Auf welchen Datenfeldern/Datenfeldgruppen wird eine bestimmte Aktion ausgeführt? 

```sparql
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX eupont: <http://elite.polito.it/ontologies/eupont.owl#>
PREFIX xdf: <https://w3id.org/GerPS-onto/FIMDatenfelder#>

Select ?element 
WHERE {
    ?sub xdf:JP000007 <https://test.schema-repository.fitko.dev/rules/baukasten/R00000042/1.0> .
    ?sub xdf:JP000008 ?element .
} 
```

[Antwort](./cq16.csv)


# 17. CQ
Welche Aktionen werden auf welchen Datenfeldern/Datenfeldgruppen in einer bestimmten Regel ausgeführt?  

```sparql
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX eupont: <http://elite.polito.it/ontologies/eupont.owl#>
PREFIX xdf: <https://w3id.org/GerPS-onto/FIMDatenfelder#>

Select ?element
WHERE {
  	?aktion xdf:JP000008 ?element .
  	?aktion ^eupont:nominalAction/^eupont:hasAction <https://test.schema-repository.fitko.dev/rules/baukasten/R00000042/1.0> .
} 
```

[Antwort](./cq17.csv)


# 18. CQ
In welchen Stammdatenschematas kommen bestimmte Datenfelder/Datenfeldgruppen vor?

```sparql
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX eupont: <http://elite.polito.it/ontologies/eupont.owl#>
PREFIX xdf: <https://w3id.org/GerPS-onto/FIMDatenfelder#>

Select * 
WHERE {
    ?Stammschemata a xdf:J000002.
    ?Stammschemata (xdf:JP000010/xdf:JP000011)+ <https://test.schema-repository.fitko.dev/groups/baukasten/G00001408/1.0> .
} 
```

[Antwort](./cq18.csv)

# 19. CQ
Welche Versionen einer bestimmten Struktur existieren?

```sparql
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX eupont: <http://elite.polito.it/ontologies/eupont.owl#>
PREFIX xdf: <https://w3id.org/GerPS-onto/FIMDatenfelder#>

Select * 
WHERE {
	<https://test.schema-repository.fitko.dev/groups/baukasten/G60000093> xdf:JP000009 ?Version .
} 
```

[Antwort](./cq19.csv)

# 20. CQ
Welche Version einer Struktur sind in einem bestimmten Stammdatenschemata enthalten? 

```sparql
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX eupont: <http://elite.polito.it/ontologies/eupont.owl#>
PREFIX xdf: <https://w3id.org/GerPS-onto/FIMDatenfelder#>

Select * 
WHERE {
  	<https://test.schema-repository.fitko.dev/schema/baukasten/S00000094/1.0> (xdf:JP000010/xdf:JP000011)+ ?Version .
    ?Version ^xdf:JP000009 <https://test.schema-repository.fitko.dev/fields/baukasten/F00000462> .
} 
```

[Antwort](./cq20.csv)
