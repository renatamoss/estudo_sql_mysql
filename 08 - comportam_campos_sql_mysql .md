## Comandos DML: Manipulação de dados com MySQL

### Campo autoincremento:
O campo *AUTO_INCREMENT* deve ter obrigatoriamente o mesmo campo como *PRIMARY KEY*.</br>
É um número sequencial que será incluído dentro da coluna de forma automática, na medida em que é dado o *INSERT.*
~~~
CREATE TABLE TAB_PADRAO
(ID INT AUTO_INCREMENT,
DESCRITOR VARCHAR(20),
ENDERECO VARCHAR(100) NULL,
CIDADE VARCHAR(50) DEFAULT 'Rio de Janeiro',
DATA_CRIACAO TIMESTAMP DEFAULT CURRENT_TIMESTAMP(),
PRIMARY KEY(ID));
~~~

### Comportamento do padrão durante o *INSERT*:

- [x] O campo *DESCRITOR*, note que depois da vírgula nada foi colocado; significa que ele será sempre obrigatório;
- [x] O campo *ENDERECO* tem um padrão *NULL*, significa que se nada foi colocado ele será nulo;
- [x] Já o campo *CIDADE*, tem como *DEFAULT* Rio de Janeiro, ou seja: se nada for incluido no Insert, o valor a ser colocado será Rio de Janeiro;
- [x] O campo *DATA_CRIACAO*, tem a função *Current Timestamp*, que dará a data e hora do computador.

<hr>


*Anotações realizados no Curso de Comandos DML: Manipulação de dados com MySQL - Alura*

