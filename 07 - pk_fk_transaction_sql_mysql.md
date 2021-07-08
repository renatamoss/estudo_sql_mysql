## Comandos DML: Manipulação de dados com MySQL

### Modelagem
O banco de dados deve ser montado conforme a modelagem. Se é 1:1 ou 1:N vai depender do tipo de negócio. 

#### Requisitos para o início da construção de um banco de dados:
- [x] Entendimento das regras de negócio;
- [x] Desenho de modelo mais fiel a realidade.

#### Passos para construção de um modelo conceitual:

- [x] Construção do diagrama de entidades e relacionamentos;
- [x] Estabelecer cardinalidade entre as entidades.

Existem ferramentas chamadas de *CASE*, que já facilitam a construção desses bancos, onde na ferramenta *CASE*, desenha-se o esquema de relações, graficamente, e automaticamente a ferramenta gera os códigos de criação.

#### Entidades do Banco de dados:

*->Tabelas(campos) ->Índice(primary key, foreign key) ->Esquemas ->View(consultas) ->Procedures e Funções ->Trigger(ordens);*

#### Usando importação de dados de arquivos externos

*-> Botão da direita do mouse sobre a tabela -> clicar Table Data Import Wizard -> Browse -> Selecionar o arquivo que será importado -> Select destination ;*

<hr>

### Criação de tabela com Primary Key:

~~~
CREATE TABLE tabela1 (
  CPF varchar(11) NOT NULL,
  NOME varchar(100) DEFAULT NULL,
  ENDERECO varchar(150) DEFAULT NULL,
  BAIRRO varchar(50) DEFAULT NULL,
  CIDADE varchar(50) DEFAULT NULL,
  ESTADO varchar(45) DEFAULT NULL,
  CEP varchar(8) DEFAULT NULL,
  DATA_NASCIMENTO date DEFAULT NULL,
  IDADE int(11) DEFAULT NULL,
  SEXO varchar(1) DEFAULT NULL,
  LIMITE_CREDITO float DEFAULT NULL,
  VOLUME_COMPRA float DEFAULT NULL,
  PRIMEIRA_COMPRA bit(1) DEFAULT NULL,
  PRIMARY KEY (CPF)
)
~~~

### Criação da FOREIGN KEY na tabela:

~~~
ALTER TABLE tabela1 ADD CONSTRAINT FK_NOME
FOREIGN KEY (CPF)
REFERENCES tabela2 (CPF);
~~~

<hr>

### COMMIT e ROLLBACK:

* #### START TRANSACTION: uma transação será inicializada;
~~~
START TRANSACTION;
UPDATE VENDEDORES SET COMISSAO = COMISSAO * 1.15;
SELECT * FROM VENDEDORES;
~~~

* #### COMMIT: confirma no banco de dados tudo aquilo que foi modificado depois do START TRANSACTION;
~~~
COMMIT;
~~~

* #### ROLLBACK: volta atrás e as modificações não são confirmadas no banco.
~~~
ROLLBACK;
~~~
<hr>

*Anotações realizados no Curso de Comandos DML: Manipulação de dados com MySQL - Alura*

