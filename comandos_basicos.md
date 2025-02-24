# Dúvidas frequentes?

| **Termo** | **O que é?** | **Analogia** |
|-----------|-------------|-------------|
| **Banco de Dados (BD)** | Conjunto de dados organizados. | Arquivo físico com várias fichas. |
| **SGBD (Sistema Gerenciador de Banco de Dados)** | Software que gerencia o banco de dados. | Funcionário que organiza as fichas. |
| **SQL (Structured Query Language)** | Linguagem usada para manipular o banco de dados. | Ordem que você dá ao funcionário para acessar as fichas. |


# Comandos Básicos do SQL

## Create

CREATE TABLE nome_tabela (
  nome_coluna tipo
)

Ex: 
CREATE TABLE clientes (
  id INT PRIMARY KEY,
  nome VARCHAR(50),
  email VARCHAR(50),
  idade INT
)

## Insert 
INSERT INTO nome_tabela (nome_coluna) VALUES (valor);

Ex: 
INSERT INTO produtos (nome, preço) VALUES ('Laptop', 1200);


## Semente para popular o banco de dados

### Criar
CREATE TABLE products (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    price DECIMAL(10,2) NOT NULL,
    stock_quantity INT NOT NULL,
    last_restocked DATE NOT NULL
);

### Popular
INSERT INTO products (name, price, stock_quantity, last_restocked) VALUES
('Notebook Dell', 4500.00, 10, '2024-02-01'),
('Mouse Logitech', 150.50, 25, '2024-02-10'),
('Teclado Mecânico', 320.90, 15, '2024-02-08');


## Update
UPDATE nome_tabela SET nome_coluna = valor WHERE condicional;

Ex:
UPDATE funcionarios SET salario = salario * 1.1 WHERE cargo = 'Gerente';

## Alter Table
ALTER TABLE tabela ADD COLUMN nome_coluna tipo;

Ex:
ALTER TABLE produtos ADD COLUMN data_cadastro DATE;

## Delete

DELETE FROM nome_tabela WHERE condicional;
Ex:
DELETE FROM pedidos WHERE status = 'Cancelado';

## Join's

### Left Join
Ex:
    SELECT clientes.nome, pedidos.id
    FROM clientes
    LEFT JOIN pedidos ON clientes.id = pedidos.cliente_id;

### Right Join
Ex:
    SELECT pedidos.id, clientes.nome
    FROM pedidos
    RIGHT JOIN clientes ON pedidos.cliente_id = clientes.id;

### Inner Join
Ex:
    SELECT pedidos.id, clientes.nome
    FROM pedidos
    INNER JOIN clientes ON pedidos.cliente_id = clientes.id;

### Diferenças

| **Tipo de JOIN** | **O que faz?** | **Registros retornados** | **Analogia** |
|-----------------|---------------|-------------------------|--------------|
| **INNER JOIN**  | Retorna apenas correspondências entre as tabelas. | Apenas registros com correspondência. | Apenas pedidos com clientes cadastrados. |
| **LEFT JOIN**   | Retorna todos os registros da tabela da esquerda e os correspondentes da direita. | Todos da esquerda, e da direita apenas os que têm correspondência. | Lista todos os clientes, mesmo que não tenham feito pedidos. |
| **RIGHT JOIN**  | Retorna todos os registros da tabela da direita e os correspondentes da esquerda. | Todos da direita, e da esquerda apenas os que têm correspondência. | Lista todos os pedidos, mesmo que não tenham um cliente associado. |

## Order by
Serve para ordernar a partir de uma condicional, por padrão é ordernado do menor para o maior (crescente).
Ex:
SELECT coluna1, coluna2
FROM tabela
ORDER BY coluna1 ASC;
 
ou

SELECT coluna1, coluna2
FROM tabela
ORDER BY coluna1 DESC;


