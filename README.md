# BDDTabela.sql

Desenvolva um banco de dados que relacione tabelas através de chaves estrangeiras ou nomes de colunas iguais. Após isso, realize todos os comandos Joins estudados.

Aqui está um exemplo de como você pode criar tabelas relacionadas por meio de chaves estrangeiras e realizar vários tipos de joins no SQL (Structured Query Language).
Criação das tabelas

CREATE TABLE clientes (
  id INT PRIMARY KEY,
  nome VARCHAR(50),
  endereco VARCHAR(100)
);

CREATE TABLE pedidos (
  id INT PRIMARY KEY,
  id_cliente INT,
  data_pedido DATE,
  FOREIGN KEY (id_cliente) REFERENCES clientes(id)
);

CREATE TABLE itens (
  id INT PRIMARY KEY,
  id_pedido INT,
  nome_produto VARCHAR(50),
  quantidade INT,
  FOREIGN KEY (id_pedido) REFERENCES pedidos(id)
);

Inserção de dados

INSERT INTO clientes (id, nome, endereco)
VALUES (1, 'João da Silva', 'Rua das Flores, 123');

INSERT INTO clientes (id, nome, endereco)
VALUES (2, 'Maria Souza', 'Rua dos Pássaros, 456');

INSERT INTO pedidos (id, id_cliente, data_pedido)
VALUES (1, 1, '2022-01-01');

INSERT INTO pedidos (id, id_cliente, data_pedido)
VALUES (2, 2, '2022-02-01');

INSERT INTO itens (id, id_pedido, nome_produto, quantidade)
VALUES (1, 1, 'Notebook', 1);

INSERT INTO itens (id, id_pedido, nome_produto, quantidade)
VALUES (2, 1, 'Mouse', 2);

INSERT INTO itens (id, id_pedido, nome_produto, quantidade)
VALUES (3, 2, 'Teclado', 1);

INSERT INTO itens (id, id_pedido, nome_produto, quantidade)
VALUES (4, 2, 'Monitor', 1);

Comandos Joins
INNER JOIN

SELECT *
FROM pedidos
INNER JOIN clientes
ON pedidos.id_cliente = clientes.id;

Resultado:

id | id_cliente | data_pedido   | id | nome          | endereco
---+-----------+--------------+----+--------------+---------
 1 | 1         | 2022-01-01   | 1  | João da Silva | Rua das Flores, 123
 2 | 2         | 2022-02-01   | 2  | Maria Souza   | Rua dos Pássaros, 456
