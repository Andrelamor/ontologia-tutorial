## SPARQL queries - para responder perguntas de competência

@prefix owl: <http://www.w3.org/2002/07/owl#> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix xml: <http://www.w3.org/XML/1998/namespace> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@dbo <http://www.semanticweb.org/andre/ontologies/2023/4/untitled-ontology-23/>

#1.qual curso é lecionado por cada professor?

SELECT ?Curso ?Professor
	WHERE { ?Curso owl:lecturedBy ?Professor }

#2.Exercício_I pertence a qual curso?

SELECT ?Curso 
	WHERE { ?Curso a Exercício_I }

(testar se implementa rdf:a como 'type')

#3.qual a titulação de cada professor?

SELECT ?title 
WHERE{
rdf:Professor owl:title ?title

#4.quantos créditos de cada disciplina?
#5.qual email de contato dos alunos? 

prefix owl: <http://www.w3.org/2002/07/owl#>
prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>

1.
SELECT ?Curso
WHERE{
	rdf:Professor owl:isLecturedBy ?Curso .
}

SELECT ?Curso
WHERE{
	dbo:Professor dbr:isLecturedBy ?Curso .
}

2.
SELECT ?Lição 
WHERE{
	rdf:Curso owl:Lição ?ExercícioI
}

3.
SELECT ?title 
WHERE{
	rdf:Professor owl:title ?title
}

