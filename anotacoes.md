# Atividade prática 11

### Relacionamento entre tabelas

- Foto das duas tabelas:
![alt text](image.png)
![alt text](image-1.png)

- Foto usando INNER JOIN:
![alt text](image-2.png)
RESPOSTA: Os alunos que não apareceram foram Sofia, Julia, Ana, Beatriz, Murilo, eles não apareceram porque não emprestaram nenhum livro.

- Foto usando LEFT JOIN:
![alt text](image-3.png)
RESPOSTA: Para quem nunca pegou um livro aparece `null` de nulo.

- A bibliotecária quer saber quem NUNCA pegou livro:
![alt text](image-4.png)
```sql
SELECT a.id, a.nome FROM alunos a WHERE NOT EXISTS ( 
    SELECT 1
    FROM emprestimos e
    WHERE e.id_alunos = a.id
);
```
- Tente registrar um empréstimo para o aluno 50:
   INSERT INTO emprestimos (livro, id_aluno) VALUES ('Turma da Mônica', 50);
Responda: o que aconteceu? Por quê?
![alt text](image-5.png)
RESPOSTA: O PostgreSQL não inseriu o empréstimo, ele cancelou o comando porque o aluno de id = 50 não existe na tabela alunos