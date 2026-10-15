# Desafio Alura - Banco de dados de Escola



## 1\. Criação de Tabelas 



### 1.1 Tabela Alunos 



CREATE table tabelaAlunos 

(ID\_aluno INT PRIMARY Key, Nome\_aluno VARCHAR(250), 

&#x20;Data\_Nascimento\_aluno DATE, genero\_aluno VARCHAR(100), 

&#x20;Endereco\_aluno VARCHAR(250), Telefone\_contato\_aluno VARCHAR, 

&#x20;Email\_aluno VARCHAR(250)

&#x20;);

&#x20;

&#x20;select \* from tabelaAlunos



### 1.2. Tabela Professores 



CREATE table tabelaProfessores 

(ID\_professor INT PRIMARY Key, Nome\_professor VARCHAR(250), 

&#x20;Data\_Nascimento\_professor DATE, genero\_professor VARCHAR(100), 

&#x20;Telefone\_contato\_professor VARCHAR, Email\_professor VARCHAR(250)

&#x20;);

&#x20;

&#x20;select \* from tabelaprofessores



### 1.3. Tabela Disciplina



CREATE table tabelaDisciplina 

(ID\_disciplina INT PRIMARY Key, Nome\_disciplina VARCHAR(250), 

Descricao\_disciplina VARCHAR(250), 

Carga\_horaria\_disciplina VARCHAR(250),

id\_professor INT,  

&#x20;FOREIGN KEY (id\_professor) REFERENCES tabelaProfessores(id\_professor)

&#x20;);

&#x20;

&#x20;SELECT \* FROM tabelaDisciplina



### 1.4. Tabela Turmas 



CREATE TABLE tabelaTurmas 

( Id\_turma INT PRIMARY KEY,

&#x20;Nome\_turma VARCHAR(50), Ano\_letivo DATE, 

&#x20;Id\_professor\_orientador INT,

FOREIGN KEY (id\_professor\_orientador) REFERENCES tabelaProfessores (id\_professor)

);



SELECT \* from tabelaTurmas



### 1.5. Tabela Turma\_Disciplina



create table TabelaTurma\_Disciplina 

( id\_turma INT, id\_disciplina INT,

&#x20; 

FOREIGN key (id\_turma) REFERENCES tabelaTurmas (id\_turma),

FOREIGN key (id\_disciplina) REFERENCES tabelaDisciplina (id\_disciplina)

);   



SELECT \* from TabelaTurma\_Disciplina



### 1.6. Tabela Turma\_Alunos

create table TabelaTurma_Alunos 
( id_turma INT, id_aluno INT,
  
FOREIGN key (id_turma) REFERENCES tabelaTurmas (id_turma),
FOREIGN key (id_aluno) REFERENCES tabelaAlunos (id_aluno)
);   

SELECT * from TabelaTurma_Alunos


### 1.7. Tabelas Notas



create table TabelaNotas 

( id\_nota, INT PRIMARY KEY, id\_aluno INT,

&#x20;id\_disciplina INT, Valor\_nota FLOAT, 

&#x20;Data\_Avaliação DATE,

&#x20; 

FOREIGN key (id\_disciplina) REFERENCES tabelaDisciplina (id\_disciplina),

FOREIGN key (id\_aluno) REFERENCES tabelaAlunos (id\_aluno)

);   



SELECT \* from TabelaNotas



## 2\. Popular as tabelas



#### Populando cada tabela com os seus respectivos dados



INSERT into TabelaNotas

(id\_nota, id\_aluno,id\_disciplina, valor\_nota, data\_avaliação )

&#x20;VALUES 

&#x20;

(2,1,1,6.19,'07/07/2023'),

(3,1,2,7.18,'07/07/2023'),

(4,1,3,7.47,'07/07/2023'),

(5,1,4,7.46,'07/07/2023'),

(6,1,5,4.35,'07/07/2023'),

(7,1,6,4.43,'07/07/2023'),

&#x20;

SELECT \* from TabelaNotas





### 3\. Visualização das colsultas



#### Consulta 1: Executar consultas para verificar se os dados foram importados corretamente em todas as tabelas.



SELECT \* FROM tabelaAlunos;

SELECT \* FROM tabelaProfessores ;

SELECT \* FROM tabelaDisciplina;

SELECT \* FROM tabelaTurmas;

SELECT \* FROM TabelaTurma\_Disciplina;

SELECT \* FROM TabelaTurma\_Alunos;

SELECT \* FROM TabelaNotas;





#### Consulta 2: Retorne as informações de todos os alunos ordenados pelo nome.



SELECT \* from tabelaAlunos ORDER BY nome\_aluno



#### Consulta 3: Retornar a disciplina que possui a carga horaria maior que 40.



select \* from TabelaDisciplina

where carga\_horaria\_disciplina > 40;



#### Consulta 4: Buscar as notas que são maiores que 6 e menores que 8.



select \* from TabelaNotas

where valor\_nota  BETWEEN  6 AND 8;

