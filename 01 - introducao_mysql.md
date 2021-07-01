 ## BANCO DE DADOS - MySQL

Dentro do banco de dados, temos diversas entidades. 
São estruturas que organizam o armazenamento do dado dentro do banco de dados.

###  -> Tabelas -> views -> procedures -> funções

<hr/>

### Tabelas: 
Uma das definições quando criamos uma tabela é definir quantos campos e o tipo de cada campo. 
Tipos de dados: 
*Texto; Número; Números com casas decimais; Números inteiros; Tipo lógico, ou seja, verdadeiro ou falso; Tipo binário, em que tenho bytes armazenados que representam, por exemplo, uma imagem, um outro arquivo com formato diferente do formato texto.*

<hr/>

### Chave primária: 
São os campos cujas combinações não podem se repetir dentro das 
 linhas da tabela ou dos registros da tabela.

<hr/>

### Índice: 
É um instrumento que permite achar elementos na tabela de maneira mais rápida.

<hr/>

### Esquemas: 
Podemos associar um grupo de tabelas ao que chamamos de esquema.
Transformar esse esquema é apenas uma maneira mais fácil de agrupar as tabelas por determinado assunto. 
É muito mais uma questão de organização.

<hr/>

### View:
Depois de montarmos as tabelas e criarmos um resultado para essa consulta, 
pode-se transformar essa consulta em uma view. Ou seja, a view tem um comportamento igual ao de uma tabela, 
só que por detrás dela já tem uma consulta construída fazendo algum tipo de regra de negócio 
para agrupar informações.

<hr/>

### Join: 
Para buscarmos informações em duas ou mais tabelas, usa-se o “join”, 
que agrupa as tabelas através de um critério.

<hr/>

### Procedures: 
São linguagens proprietárias que permitem com que consigamos, usando comandos de SQL, 
fazer algum tipo de lógica estruturada, através de ifs, whiles e vários comandos de repetição. 
É como se fizéssemos um programa em uma linguagem nativa do banco de dados utilizando comandos de SQL.

<hr/>

### Funções: 
Dentro das procedures, posso também ter funções. 
As funções são cálculos feitos com os campos. Normalmente, ela entra com o parâmetro campos. 
E depois é possível usar essa função dentro de um comando de consulta.

<hr/>

### Trigger: 
É um aviso, um alerta que programo caso alguma coisa aconteça no banco de dados ou na tabela. 

<hr/>


*Anotações feitas no Curso de Introdução ao SQL com MySQL: Manipule e consulte dados - Alura*

