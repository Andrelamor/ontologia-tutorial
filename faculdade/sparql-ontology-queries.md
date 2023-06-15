## SPARQL queries - para responder pergnutas de competência

#1.qual curso é lecionado por cada professor?

SELECT ?Curso ?Professor
	WHERE { ?Curso owl:lecturedBy ?Professor }

#2.Exercício_I pertence a qual curso?

SELECT ?Curso 
	WHERE { ?Curso a Exercício_I }

#3.qual a titulação de cada professor?
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

