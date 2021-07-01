## MySQL - Manipulando e consultando dados com SQL
### MySQL PELA LINHA COMANDO:
~~~
C:\Program Files\MySQL\MySQL Server 8.0\bin>mysql -h localhost -u root -p 
~~~
### Criando um banco de dados:
~~~
CREATE DATABASE nome;
~~~
### Deletando um banco de dados:
~~~
DROP DATABASE nome;
~~~
### Acessando um banco de dados:
~~~
SELECT * FROM nome;
~~~
### Criando uma tabela:
~~~
USE nome do banco;

CREATE table tbproduto  
(PRODUTO VARCHAR(10), 
NOME VARCHAR(50),  
EMBALAGEM VARCHAR(50),  
TAMANHO VARCHAR(50),  
SABOR VARCHAR(50), 
PRECO_LISTA FLOAT);  
~~~
### Apagando uma tabela:
~~~
DROP TABLE nome;
~~~
### Inserindo dados na tabela:
~~~
INSERT INTO tbproduto (  
produto, nome, embalagem, tamanho, sabor, preco_lista) 
values ('1040107', 'Light - 350ml - Melância',  'lata', '350 ml', 'Melância', 4.56);
~~~
### Tipos de consulta da tabela:
~~~
SELECT * FROM tbproduto; 
SELECT CPF, NOME FROM tbcliente; 
SELECT CPF, NOME FROM tbcliente LIMIT 2; 
SELECT * FROM tbproduto WHERE PRODUTO = '1096818'; 
SELECT * FROM tbcliente WHERE CIDADE = 'Rio de Janeiro'; 
SELECT * FROM tbcliente WHERE IDADE >= 22; 
~~~
### Consultando um dado na tabela tipo data:
~~~
SELECT * FROM tbcliente WHERE DATA_NASCIMENTO = '1995-01-13'  
SELECT * FROM tbcliente WHERE DATA_NASCIMENTO > '1995-01-13' 
SELECT * FROM tbcliente WHERE YEAR(DATA_NASCIMENTO) = 1995; 
SELECT * FROM tbcliente WHERE month(DATA_NASCIMENTO) = 10;
~~~
### Consultando um dado na tabela tipo float:
~~~
SELECT * FROM tbproduto WHERE PRECO_LISTA BETWEEN 6.30 AND 6.31;
~~~
### ALIAS: É um nome fantasia dado ao campo:
~~~
SELECT CPF AS CPF_CLIENTE, NOME AS NOME_CLIENTE FROM tbcliente;
~~~
### Filtros compostos:
~~~
SELECT * FROM tbcliente WHERE month(DATA_NASCIMENTO) = 10 AND SEXO = 'M'; 
SELECT * FROM tbcliente WHERE month(DATA_NASCIMENTO) = 10 OR SEXO = 'M'; 
~~~
### Alterando dados na tabela:
~~~
UPDATE tbproduto SET embalagem = 'lata', preco_lista = '4.88' WHERE produto = '1004327';
UPDATE tbproduto SET SABOR= 'Cítricos' WHERE SABOR = 'Limão';
~~~
### Excluindo dados na tabela:
~~~
DELETE FROM tbproduto WHERE PRODUTO = '1004327';
~~~
### Inserindo um novo campo na tabela:
~~~
ALTER TABLE tbcliente ADD COLUMN (DATA_NASCIMENTO DATE);
~~~
### Inserindo a chave primária na tabela:
*(Alterando o campo produto JÁ existente para primary key)*  
~~~
ALTER TABLE tbproduto ADD PRIMARY KEY (PRODUTO);  
~~~

<hr/>

*Anotações feitas no Curso de Introdução ao SQL com MySQL: Manipule e consulte dados - Alura*