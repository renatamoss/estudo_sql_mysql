## MySQL - Consultas SQL: Avançando no SQL com MySQL

### Importanto dados externos para o banco de dados:

*-> Selecione o banco -> Administration -> Management/Data Import/Restore -> Selecione o Arquivo*
*-> Start Import -> Refresh All;*

<hr/>

### Esquemas de dados: a estrutura do banco de dados:

Consultando a tabela no modo visual: 
*-> Database -> Reverse Engineer;*

<hr/>

### Alguns filtros condicionais: 
~~~
SELECT * FROM tabela_de_clientes WHERE PRECO_DE_LISTA BETWEEN 6 AND 7;
SELECT * FROM tabela_de_clientes WHERE sabor = 'manga' AND tamanho = '470 ml';
SELECT * FROM tabela_de_clientes WHERE NOT (sabor = 'manga');
SELECT * FROM tabela_de_clientes WHERE sabor IN ('laranja', 'manga');
SELECT * FROM tabela_de_clientes WHERE CIDADE IN ('Rio de Janeiro', 'São Paulo') AND IDADE >= 20;
SELECT * FROM tabela_de_clientes WHERE CIDADE IN ('Rio de Janeiro', 'São Paulo') AND (IDADE >= 20 AND IDADE <= 22);
~~~

<hr/>

### LIKE: busca dado que possui o trecho que está entre os % %, na descrição:
~~~
SELECT * FROM tabela_de_produtos WHERE SABOR LIKE '%Maça%' AND EMBALAGEM = 'PET';
~~~

<hr/>

### DISTINCT: busca os dados que não se repetem na tabela:
~~~
SELECT DISTINCT EMBALAGEM, TAMANHO FROM tabela_de_produtos WHERE SABOR = 'laranja';
~~~

<hr/>

### LIMIT: limite na posição máxima, ou começa na posição informada até o máximo da posição:
~~~
SELECT * FROM notas_fiscais WHERE DATA_VENDA = '2017-01-01' LIMIT 10;
SELECT * FROM tabela_de_produtos LIMIT 2,3;
~~~

<hr/>

### ORDER BY: a ordenação começa do maior para o menor OU menor para o maior; 
*Também pode-se aplicar as condições DESC - descendente e ASC - ascendente;*

~~~
SELECT * FROM tabela_de_produtos ORDER BY EMBALAGEM, NOME_DO_PRODUTO;
SELECT * FROM tabela_de_produtos ORDER BY EMBALAGEM DESC, NOME_DO_PRODUTO ASC;
SELECT * FROM itens_notas_fiscais WHERE codigo_do_produto = '1101035' ORDER BY QUANTIDADE DESC;
~~~

<hr/>

### Comandos SUM, MAX, COUNT: Aplicando critério de agrupamento sobre os campos numéricos:

- [X] SUM: soma o total do campo especificado no GROUP BY;
- [X] MAX: busca o valor máximo do campo especificado no GROUP BY;
- [X] COUNT(*): conta a quantidade dos diferentes tipos especificado no campo GROUP BY.

~~~
SELECT ESTADO, SUM(LIMITE_DE_CREDITO) AS LIMITE_TOTAL FROM tabela_de_clientes GROUP BY ESTADO;
SELECT EMBALAGEM, MAX(PRECO_DE_LISTA) AS MAIOR_PRECO FROM tabela_de_produtos GROUP BY EMBALAGEM;
SELECT EMBALAGEM, COUNT(*) AS CONTADOR  FROM tabela_de_produtos GROUP BY EMBALAGEM;
~~~

<hr/>

### Agrupando, filtrando e ordenando os dados no mesmo comando:
~~~
SELECT ESTADO, BAIRRO, SUM(LIMITE_DE_CREDITO) AS LIMITE_TOTAL FROM tabela_de_clientes 
WHERE CIDADE = 'Rio de Janeiro'
GROUP BY ESTADO, BAIRRO
ORDER BY BAIRRO;
~~~

<hr/>

### HAVING: é um filtro que não se aplica sobre o SELECT, mas sobre o resultado de um SELECT que é agrupado: 

~~~
SELECT CPF, COUNT(*) FROM notas_fiscais
WHERE YEAR(DATA_VENDA) = 2016
GROUP BY CPF
HAVING COUNT(*) > 2000;
~~~

<hr/>

### CASE: condicional se acontece uma determinada condição, executa; senão, executa outra:

~~~
SELECT NOME_DO_PRODUTO, PRECO_DE_LISTA,
CASE
   WHEN PRECO_DE_LISTA >= 12 THEN 'PRODUTO CARO'
   WHEN PRECO_DE_LISTA >= 7 AND PRECO_DE_LISTA < 12 THEN 'PRODUTO EM CONTA'
   ELSE 'PRODUTO BARATO'
END AS STATUS_PRECO
FROM tabela_de_produtos;
~~~

<hr/>

*Anotações feitas no Curso de MySQL - Consultas SQL: Avançando no SQL com MySQL - Alura*

