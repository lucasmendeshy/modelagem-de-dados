## Etapa 03


### 1) Faça uma consulta que mostre os alunos que nasceram antes do ano 2009
```SQL 

 SELECT nome,nasc FROM alunos WHERE nasc < 2009; 
```

### 2 Faça uma consulta que calcule a média das notas de cada aluno e as mostre com duas casas decimais.
```SQL  

SELECT nome, primeira_nota, segunda_nota, ROUND( (primeira_nota + segunda_nota)/2, 2) AS Média FROM alunos;
```

### 3) Faça uma consulta que calcule o limite de faltas de cada curso de acordo com a carga horária. Considere o limite como 25% da carga horária. Classifique em ordem crescente pelo título do curso.

```sql

SELECT titulo, carga_horaria (carga_horaria * 0,25) AS "Limite de falta" FROM cursos;
```

### 4) Faça uma consulta que mostre os nomes dos professores que são somente da área "desenvolvimento".
``` SQL

 SELECT nome, atuacao FROM professores WHERE curso_id = 13 OR curso_id = 14;
```

### 5) Faça uma consulta que mostre a quantidade de professores que cada área ("design", "infra", "desenvolvimento") possui.
``` SQL

SELECT atuacao, COUNT(atuacao) AS "Área de atuação" from professores GROUP BY atuacao;
```

### 6) Faça uma consulta que mostre o nome dos alunos, o título e a carga horária dos cursos que fazem.
``` SQL

 SELECT
 alunos.nome, cursos.titulo, cursos.cargaHoraria FROM alunos INNER JOIN cursos ON alunos.curso_id = cursos.id ORDER BY alunos.nome;
```



### 7) Faça uma consulta que mostre o nome dos professores e o título do curso que lecionam. Classifique pelo nome do professor.
```SQL
 
 SELECT professores.nome, cursos.titulo FROM professores INNER JOIN cursos ON professores.curso_id = cursos.id ORDER BY professores.nome;
```



### 8) Faça uma consulta que mostre o nome dos alunos, o título dos cursos que fazem, e o professor de cada curso.
```SQL
 
 SELECT alunos.nome, cursos.titulo, professores.atuacao FROM alunos INNER JOIN cursos ON alunos.curso_id = cursos.id INNER JOIN professores ON professores.curso_id = cursos.id;
```

### 9) Faça uma consulta que mostre a quantidade de alunos que cada curso possui. Classifique os resultados em ordem descrecente de acordo com a quantidade de alunos.
```SQL
 
 SELECT COUNT(alunos.curso_id) AS "Cursos", cursos.titulo AS Cursos FROM alunos INNER JOIN cursos ON alunos.curso_id = cursos.id GROUP BY cursos.titulo ORDER BY COUNT(alunos.curso_id) DESC;
```

### 10) Faça uma consulta que mostre o nome dos alunos, suas notas, médias, e o título dos cursos que fazem. Devem ser considerados somente os alunos de Front-End e Back-End. Mostre classificados pelo nome do aluno
```SQL
 
SELECT alunos.nome, alunos.primeira_nota, alunos.segunda_nota, cursos.titulo, ROUND( (primeira_nota + segunda_nota)/2 ) AS Média FROM alunos INNER JOIN cursos ON alunos.curso_id = cursos.id WHERE curso_id = 10 OR curso_id = 11 ORDER BY alunos.nome; 
```

### 11) Faça uma consulta que altere o nome do curso de Figma para Adobe XD e sua carga horária de 10 para 15.
``` SQL

UPDATE cursos 
SET 
titulo = "Adobe XD",
cargaHoraria = 15
WHERE
id = 13;
```

### 12) Faça uma consulta que exclua um aluno do curso de Redes de Computadores e um aluno do curso de UX/UI.
``` SQL

DELETE alunos WHERE id = 6 OR id = 9;
```


### 13) Faça uma consulta que mostre a lista de alunos atualizada e o título dos cursos que fazem, classificados pelo nome do aluno.
```SQL

SELECT alunos.nome, cursos.titulo FROM alunos INNER JOIN cursos ON alunos.curso_id = cursos.id ORDER BY alunos.nome DESC;
```
