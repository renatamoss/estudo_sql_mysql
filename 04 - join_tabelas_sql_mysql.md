## Consultas SQL: Avançando no SQL com MySQL

### JOIN: Permite juntar duas ou mais tabelas, dentro de um único comando SQL:
- [X] Os JOINs são feitos através de um campo comum entre todas as tabelas;
~~~
SELECT * FROM tabela_de_vendedores A
JOIN notas_fiscais B
ON A.MATRICULA = B.MATRICULA;
~~~

- [X] No INNER JOIN pode-se aplicar também o GROUP BY. </br>
A cláusula GROUP BY é responsável por determinar em quais grupos devem ser colocadas as linhas de saída.</br>
No exemplo abaixo, todas as matrículas serão agrupadas em linhas individuais:
~~~
SELECT A.MATRICULA, A.NOME, COUNT(*) AS QTDE_VENDAS
FROM tabela_de_vendedores A
INNER JOIN notas_fiscais B
ON A.MATRICULA = B.MATRICULA
GROUP BY MATRICULA;
~~~
*O resultado será a quantidade total de notas emitidas, onde as notas emitidas por vendedor estão na tabela notas_fiscais, e os vendedores (nome e matrícula) estão na tabela_de_vendedores.*

- [x] LEFT JOIN: traz os dados que estão na esquerda, e somente os correspondentes da direita;
- [x] RIGHT JOIN: traz todos os dados da direita, mas somente os correspondentes da esquerda;
~~~
SELECT DISTINCT A.CPF, A.NOME, B.CPF 
FROM tabela_de_clientes A
LEFT JOIN notas_fiscais B 
ON A.CPF = B.CPF
~~~
- [x] WHERE - IS NULL: traz somente quem tem o filtro solicidado nulo naquela tabela;
~~~
SELECT DISTINCT A.CPF, A.NOME, B.CPF 
FROM tabela_de_clientes A
LEFT JOIN notas_fiscais B ON A.CPF = B.CPF
WHERE B.CPF IS NULL;
~~~

- [x] FULL JOIN: irá mostrar todos os registros das duas tabelas, correspondendo ou não. <br>
O FULL JOIN no MySQL pode ser simulado usando um LEFT com RIGHT, com UNION no meio.
~~~
SELECT tabela_de_vendedores.BAIRRO,
tabela_de_vendedores.NOME, DE_FERIAS,
tabela_de_clientes.BAIRRO,
tabela_de_clientes.NOME  FROM tabela_de_vendedores LEFT JOIN tabela_de_clientes
ON tabela_de_vendedores.BAIRRO = tabela_de_clientes.BAIRRO
UNION
SELECT tabela_de_vendedores.BAIRRO,
tabela_de_vendedores.NOME, DE_FERIAS,
tabela_de_clientes.BAIRRO,
tabela_de_clientes.NOME  FROM tabela_de_vendedores RIGHT JOIN tabela_de_clientes
ON tabela_de_vendedores.BAIRRO = tabela_de_clientes.BAIRRO;
~~~

<hr/>

### UNION:
O UNION é o comando que une duas consultas. O UNION simples une e faz ao mesmo tempo o DISTINCT;
~~~
SELECT DISTINCT BAIRRO FROM tabela_de_clientes
UNION
SELECT DISTINCT BAIRRO FROM tabela_de_vendedores;
~~~

UNION ALL: não se aplica o DISTINCT. Lista todos os registros de duas ou mais tabelas, listando inclusive os repetidos.
~~~
SELECT DISTINCT BAIRRO FROM tabela_de_clientes
UNION ALL
SELECT DISTINCT BAIRRO FROM tabela_de_vendedores;
~~~

<hr/>

### SUB-CONSULTAS: 
As sub-consultas permitem que possa ser feita seleções usando como critérios outras seleções:
~~~
SELECT * FROM tabela_de_clientes WHERE BAIRRO 
IN (SELECT DISTINCT BAIRRO FROM tabela_de_vendedores);
~~~

<hr/>

### View: é uma tabela lógica: 
É possível salvar uma query pronta, essa query pode ser simples ou complexa, e também referenciar essa visão como se fosse uma tabela. Deve-se salvar com um nome, X, por exemplo, e dar um SELECT asterisco FROM X.

*-> View -> Create View -> Apply* -> criar a View `VW_MAIORES_EMBALAGEN´

~~~
SELECT X.EMBALAGEM, X.PRECO_MAXIMO FROM 
(SELECT EMBALAGEM, MAX(PRECO_DE_LISTA) AS PRECO_MAXIMO FROM tabela_de_produtos
GROUP BY EMBALAGEM) X WHERE X.PRECO_MAXIMO >= 10;
~~~

Será substituído por:

~~~
SELECT X.EMBALAGEM, X.PRECO_MAXIMO FROM 
VW_MAIORES_EMBALAGENS X WHERE X.PRECO_MAXIMO >= 10;
~~~

<hr/>

*Anotações feitas no Curso de MySQL - Consultas SQL: Avançando no SQL com MySQL - Alura*

