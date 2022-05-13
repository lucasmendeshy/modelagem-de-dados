# Comandos SQL para CRUD - Referência

## Resumo

- C -> Create (inserir dados)
- R -> Read (ler dados)
- U -> Update (atualizar dados)
- D -> Delete (excluir dados)


## INSERT

### Fabricantes

``` sql
INSERT INTO fabricantes (nome) VALUES('Asus');
INSERT INTO fabricantes (nome) VALUES('Dell');
INSERT INTO fabricantes (nome)
 VALUES('Apple'), ('LG'), ('Samsung'), ('Brastemp');
```


### Produtos

``` SQL
INSERT INTO produtos(nome,descricao,preco,quantidade,fabricante_id) VALUES (
     'Ultrabook',
     'Ultrabook Asus com processador Intel Core i12, memória RAM de 16GB e Windows 11',
     6500.99,
     7,
     1
);
```


``` SQL
INSERT INTO produtos(nome,descricao,preco,quantidade,fabricante_id) VALUES (
     'Tablet Android',
     'Tablet com a versão 12 do sistema operacional da Google, possui tela de 10 polegadas e armazenamento de 64 GB',
     4999,
     3,
     5 -- Samsung
);

``` 

``` SQL
INSERT INTO produtos(nome,descricao,preco,quantidade,fabricante_id) VALUES (
     'Geladeira',
     'Refrigerador Frost-free com acesso à internet das Coisas e bla bla bla',
     4999,
     3,
     6 -- Brastemp
),

(
    'Iphone 13 Pro Max',
    'Alta durabilidade, processador Bionic 14, 128GB de armazenamento, 6 de RAM e caro pra caramba',
    6999.99,
    3,
    3 -- Apple
),

(
    'iPad Mini',
    'Tablet Apple com tela retina display de 4k, memória interna de 64GB, acesso ao Icloud.',
    5000,
    8,
    3 -- Apple
);
```




## INSERT - EXERCICIO

### Fabricantes
``` SQL
INSERT INTO fabricantes (nome) VALUES ('Positivo');
INSERT INTO fabricantes (nome) VALUES ('Microsoft');
```


### Produtos

``` SQL
INSERT INTO produtos(nome,descricao,preco,quantidade,fabricante_id) VALUES (
     'Xbox One',
     'Console de ultima geração com acesso aos melhores jogos.',
     2500,
     5,
     8
),

(
    'Ultrabook',
    'Ultrabook equipamento com processador AMD Ryzen 5, 12GB de RAM, placa de vídeo RTX.',
    4500.68,
    4,
    7
);
```

## SELECT

### Ler dados da tabele produtos

``` SQL
SELECT * FROM produtos;
SELECT nome, preco FROM produtos;
SELECT preco, nome FROM produtos WHERE preco < 5000;
SELECT nome, descricao FROM produtos WHERE fabricante_id = 3; -- Apple
```


### Operadores Lógicos: E OU NÃO


``` SQL
SELECT * FROM produtos WHERE preco >= 5000 AND preco < 8000;

SELECT nome, preco  FROM produtos WHERE fabricante_id = 3 OR fabricante_id = 8;

SELECT nome, preco, quantidade FROM produtos WHERE fabricante_id = 1 OR fabricante_id = 5 OR fabricante_id = 6 OR fabricante_id = 7 OR fabricante_id = 8; -- VERSÃO 3
-- WHERE NOT fabricante_id = 3; - VERSÃO 1 USANDO NOT
-- WHERE NOT fabricante_id != 3;  VERSÃO 2 - USANDO OPERADOR !=
-- WHERE fabricante_id IN (3, 8); - USANDO FUNÇÃO IN (lista)
```

### Filtros

```SQL
SELECT nome, preco FROM produtos ORDER BY nome; -- ASC
SELECT nome, preco FROM produtos ORDER BY nome DESC;

-- ASC -> ordenação em modo crescente (padrão)
-- DESC -> ordenação em modo decrescente 

SELECT nome, descricao FROM produtos WHERE descricao LIKE '%processador%'; -- LIKE (COMO)
-- % OPERADOR CORINGA (SIGNIFICA QUALQUER TEXTO)
```

### Operações e Funções de agregação

```SQL
SELECT SUM(preco) FROM produtos; -- soma
SELECT SUM(preco) AS TOTAL -- AS É UM ALIAS (APELIDO)
FROM produtos;

SELECT SUM(quantidade) AS "Quantidade em estoque"
FROM produtos WHERE fabricante_id = 3; -- Apple

-- AVG (AVERAGE) MÉDIA
SELECT AVG(preco) AS "Média dos preços" -- Apelido
FROM produtos; 

-- ROUND (Arredondamento)
SELECT ROUND( AVG (preco),2 ) AS "Média dos preços"
FROM produtos; 

-- COUNT (Contagem)
SELECT COUNT(id) AS "Quantidade de produtos"
FROM produtos;

-- DISTINCT é um comando para evitar a duplicidade na contagem de campos que nao são chave-primária
SELECT COUNT(DISTINCT fabricante_id) AS "Quantidade de fabricante"
FROM produtos;


SELECT nome, preco,quantidade, (preco * quantidade) AS Total
 FROM produtos;
```

 
``` SQL 
-- INSERINDO NOVOS FABRICANTES

-- INSERT INTO `produtos` (`id`, `nome`, `descricao`, `preco`, `quantidade`, `fabricante_id`) VALUES (NULL, 'Teclado Gamer', 'Teclado de última geração com teclas quânticas e mecânicas ótimo tempo de resposta e bla bla bla. Ah! E led embutido!', '380', '8', '8'), (NULL, 'Placa-mãe', 'Placa com diversos slots de memória RAM DDR6, suporte a processadores Intel linha Core I5 e i7.', '1200', '5', '1')
```


### Agrupamentos

``` SQL
SELECT fabricante_id, SUM(preco) AS Total FROM produtos
GROUP BY fabricante_id;
--GROUP BY permite segmentar resultados da consulta. Neste caso, somamos todos os preços e segmentamos/agrupamos por cada fabricante.
 
```


## Update

### Atualizar dados de uma tabela

``` SQL
UPDATE fabricantes SET nome = 'Microsoft Brasil'
WHERE id = 8;

-- Mudar o preço do Ultrabook da positivo para 5200.

UPDATE produtos SET preco = 5200
WHERE id = 7;

-- Mudar a quantidade dos produtos da Asus e da Apple para 15.
UPDATE produtos SET quantidade = 15
WHERE fabricante_id= 1 OR fabricante_id = 3;
```


### Excluir dados de uma tabela

``` SQL
-- LG
DELETE FROM fabricantes WHERE id = 4; 

DELETE FROM produtos
WHERE preco <= 2000 AND preco > 500;
```


### Consulta de dados de duas ou mais tabelas (JUNÇÃO)

```SQL
-- nomeDaTabela.nomeDaColuna
SELECT produtos.nome,  fabricantes.nome

-- INNER JOIN é o comando que permite juntar tabelas para uma consulta.
FROM produtos INNER JOIN fabricantes

-- ON comando para indicar o critério da junção
ON produtos.fabricante_id = fabricante.id;

-- Nome do Produto e do Fabricante, ordenados pelo nome do produto

SELECT
  produtos.nome AS Produtos,
  fabricantes.nome AS Fabricante

FROM produtos INNER JOIN fabricantes
ON produtos.fabricante_id = fabricantes.id 
ORDER BY produtos.nome, fabricantes.nome;

-- Fabricante, soma dos preços e quantidade dos produtos    

SELECT 
fabricantes.nome AS Fabricante,
SUM(produtos.preco) AS Total,
COUNT(produtos.fabricante_id) AS "Qtd de produtos"
FROM produtos INNER JOIN fabricantes
ON produtos.fabricante_id = fabricantes.id
GROUP BY Fabricante
ORDER BY Total;

-- Trazer a quantidade de produtos de cada fabricante

SELECT 
     fabricantes.nome AS Fabricante,
    COUNT(produtos.fabricante_id) AS Quantidade

-- INNER JOIN -> traz os registros somente daqueles fabricantes que tem produtos 

    FROM produtos INNER JOIN fabricantes ON produtos.fabricante_id = fabricantes.id
    GROUP BY Fabricante;

SELECT 
     fabricantes.nome AS Fabricante,
    COUNT(produtos.fabricante_id) AS Quantidade

-- RIGHT/LEFT -> traz os registros mesmo daqueles fabricantes que não tem produtos

    FROM produtos RIGHT JOIN fabricantes ON produtos.fabricante_id = fabricantes.id
    GROUP BY Fabricante;

```







