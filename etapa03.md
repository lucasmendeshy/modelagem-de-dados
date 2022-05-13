## Etapa 03

```SQL 
-- Exercício 1
 SELECT nome,nasc FROM alunos WHERE nasc < 2009; 
```



```SQL  

-- Exercício 2

--Exercício 3


-- Exercicio 4

 SELECT nome, atuacao FROM professores WHERE curso_id = 13 OR curso_id = 14;


-- Exercício 5



-- Exercício 6

 SELECT
 alunos.nome, cursos.titulo, cursos.cargaHoraria FROM alunos INNER JOIN cursos ON alunos.curso_id = cursos.id ORDER BY alunos.nome;

 -- Exercício 7

 SELECT professores.nome, cursos.titulo FROM professores INNER JOIN cursos ON professores.curso_id = cursos.id ORDER BY professores.nome;

 -- Exercício 8

 SELECT alunos.nome, cursos.titulo, professores.atuacao FROM alunos INNER JOIN cursos ON alunos.curso_id = cursos.id INNER JOIN professores ON professores.curso_id = cursos.id;

 -- Exercício 9

 SELECT COUNT(alunos.curso_id) AS "Quantidade", cursos.titulo AS Cursos FROM alunos INNER JOIN cursos ON alunos.curso_id = cursos.id GROUP BY cursos.titulo ORDER BY COUNT(alunos.curso_id) DESC;

 -- Exercício 10 

 SELECT alunos.nome AS Nome, alunos. 








```