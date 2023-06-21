# LOG dos passos para configuração de servidor e execução das queries do SPARQL

- foi necessário utilizar um servidor diferente para rodar as queries do SPARQL, pois o servidor nativo do Protegè para essa tarefa não estava rodando (referências:)

- segundo [aula do Thiago da FALE](), o servidor Apache-Jena-Fuseki seria a melhor alternativa de servidor SPARQL para executar as queries/perguntas de competência de uma ontologia 

## erro do java

````
Andre@DESKTOP-R63LP8N MINGW64 ~/Desktop/apache-jena-fuseki-4.8.0
$ ./fuseki-server
Invalid maximum heap size: -Xmx4G
The specified size exceeds the maximum representable size.
Error: Could not create the Java Virtual Machine.
````
- mesmo executando um workaround com os passos
	- desinstalando e reinstalando o java após reiniciar o windows
	- aumentando a memória da máquina virtual do java como variável de ambiente do windows
	- executando o Java como administrador

...o fuseki-server não rodou;

- a versão corrente do FUSEKI (4.8 - ver mais recente em https://github.com/apache/jena/tags) exige o Java 11; a versão do Java na máquina era a 8.1.371;

- foi necessário então instalar a versão 3.15, a mesma utilizada pelo Thiago na aula 8.1, disponível em https://archive.apache.org/dist/jena/binaries/

# perguntas de competência - testes SPARQL

## 1. qual professor titular organiza o curso Web_Semântica?

````
SELECT ?ProfessorTitular
WHERE {
  ?ProfessorTitular teste:organizes teste:Web_Semântica .
}
````

- Resultado: `No data available in table`
	- hipóteses: a. PREXIX 'teste' com a IRI da ontologia no Protegè não captado
				 b. query incorreta

## 2. quais os professores existentes?

````
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX dbo: <http://www.semanticweb.org/andre/ontologies/2023/4/untitled-ontology-23>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
SELECT ?Professor
WHERE {
  dbo:type dbo:Professor ?Professor .
}

````
- Resultado: `No data available in table`

#### 2.1. quais os professores titulares existentes?

````
SELECT ?ProfessorTitular
WHERE {
  ?ProfessorTitular rdf:type teste:ProfessorTitular .
}
````
- Resultado: `No data available in table`
	- hipóteses: a. PREXIX 'teste' com a IRI da ontologia no Protegè não captado (falta prexiso XML? O prefixo .ttl não foi carregado;~ainda não consegui gerar o turtle com o label dos types como prefixo legível a olho humano)
				 b. query incorreta

````
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX dbo: <http://www.semanticweb.org/andre/ontologies/2023/4/untitled-ontology-23>
SELECT ?ProfessorTitular
WHERE {
  ?ProfessorTitular dbo:Type dbo:ProfessorTitular .
}
````
- Resultado: `No data available in table`

````
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX dbo: <http://www.semanticweb.org/andre/ontologies/2023/4/untitled-ontology-23>
SELECT ?ProfessorTitular
WHERE {
  ?ProfessorTitular rdf:Type dbo:ProfessorTitular .
}
````
- Resultado: `No data available in table`

## 3. qual professor leciona Ontologia?
````
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX dbo: <http://www.semanticweb.org/andre/ontologies/2023/4/untitled-ontology-23>
PREFIX xml: <http://www.w3.org/XML/1998/namespace>
SELECT ?Professor
WHERE {
  dbo:lectures dbo:Ontologia ?Professor .
}
````
