```sql
-- 1) Faça uma consulta que mostre os alunos que nasceram antes do ano 2009
select * from alunos where nascimento < "2009-01-01"; 

----------------------------------------------------------------------------------------------------------------------
-- 2) Faça uma consulta que calcule a média das notas de cada aluno e as mostre com duas casas decimais. 
select nome,round((nota1 + nota2)/2 , 2) as "média" from alunos 


----------------------------------------------------------------------------------------------------------------------
-- 3) Faça uma consulta que calcule o limite de faltas de cada curso de acordo com a carga horária. Considere o limite como 25% da carga horária. Classifique em ordem crescente pelo título do curso.
 select cursos.titulo, (cargahoraria * 0.25) as "qtd de faltas" from cursos 
 order by titulo 

----------------------------------------------------------------------------------------------------------------------
-- 4) Faça uma consulta que mostre os nomes dos professores que são somente da área "desenvolvimento".
 select professores.nome as nome, professores.area as área  from professores where area = 'desenvolvimento' 

----------------------------------------------------------------------------------------------------------------------
-- 5) Faça uma consulta que mostre a quantidade de professores que cada área ("design", "infra", "desenvolvimento") possui.
 select area as Area , count(*) as quantidade from professores 
 group by area
 
----------------------------------------------------------------------------------------------------------------------
-- 6) Faça uma consulta que mostre o nome dos alunos, o título e a carga horária dos cursos que fazem.
select alunos.nome, cursos.titulo , cursos.cargahoraria from alunos 
INNER join cursos on alunos.cursos_id = cursos.id;

----------------------------------------------------------------------------------------------------------------------
-- 7) Faça uma consulta que mostre o nome dos professores e o título do curso que lecionam. Classifique pelo nome do professor. 
select professores.nome, cursos.titulo from professores 
inner join cursos on professores.cursos_id = cursos.id 
order by nome

----------------------------------------------------------------------------------------------------------------------
-- 8) Faça uma consulta que mostre o nome dos alunos, o título dos cursos que fazem, e o professor de cada curso.
select alunos.nome , cursos.titulo, professores.nome from alunos
inner join cursos on alunos.cursos_id = cursos.id
inner join professores on cursos.professores_id = professores.id

----------------------------------------------------------------------------------------------------------------------
-- 9) Faça uma consulta que mostre a quantidade de alunos que cada curso possui. Classifique os resultados em ordem descrecente de acordo com a quantidade de alunos.
select cursos.titulo count(alunos.cursos_id) as "qtd de alunos" from cursos 
inner join alunos on alunos.cursos_id = cursos.id  
group by cursos.titulo 
order by "qtd de alunos" desc

----------------------------------------------------------------------------------------------------------------------
-- 10) Faça uma consulta que mostre o nome dos alunos, suas notas, médias, e o título dos cursos que fazem. Devem ser considerados somente os alunos de Front-End e Back-End. Mostre os resultados classificados pelo nome do aluno.
select alunos.nome as nome,cursos.titulo, alunos.nota1 as nota1, alunos.nota2 as nota2, round((nota1 + nota2)/2, 2) as "média" from alunos 
inner join cursos on alunos.cursos_id = cursos.id where cursos.id in(16, 17)
order by (nome)

----------------------------------------------------------------------------------------------------------------------
--11) Faça uma consulta que altere o nome do curso de Figma para Adobe XD e sua carga horária de 10 para 15.
update cursos set titulo = "Adobe XD", cargahoraria = 15 where id=19
select cursos.titulo , cursos.cargahoraria from cursos

----------------------------------------------------------------------------------------------------------------------
--12) Faça uma consulta que exclua um aluno do curso de Redes de Computadores e um aluno do curso de UX/UI.
delete from alunos where id in (18,19)

----------------------------------------------------------------------------------------------------------------------
--13) Faça uma consulta que mostre a lista de alunos atualizada e o título dos cursos que fazem, classificados pelo nome do aluno.
select alunos.nome, cursos.titulo from alunos 
inner join cursos on alunos.cursos_id = cursos.id
order by nome
```