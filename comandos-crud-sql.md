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




## INSERT

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