## Modelagem Física

### Criando banco de dados

``` SQL
CREATE DATABASE cinema CHARACTER SET utf8mb4;
```

### Criando tabela genero

``` SQL
CREATE TABLE genero(
    id INT NOT NULL PRIMARY KEY  AUTO_INCREMENT,
    genero VARCHAR(45) NOT NULL 
);
```

## Criando tabela filmes

``` SQL
CREATE TABLE filmes(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(45) NOT NULL,
    lancamento YEAR(2001) NOT NULL,
    genero_id INT NOT NULL
);
```
### Criação da chave estrangeira (relacionamento entre as tabelas)


``` SQL
ALTER TABLE filmes

ADD CONSTRAINT fk_filmes_genero

FOREIGN KEY(genero_id) REFERENCES filmes(id);
```