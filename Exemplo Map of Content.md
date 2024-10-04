---
tags:
  - "#moc"
---
Lets do this 🤟👨‍🔬🧛

# Exemplo de Map of Content

Este arquivo funciona como um grande "saco de conteúdo" onde vc organiza o que existe no seu Vault. Na visão do obsidian, folders e arquivos são secundários na organização do conteúdo. 

Use e abuse de Hashtags, Atributos, Buscas e Links para viabilizar o seu próprio mapa de conhecimento.

---

![[Minibio#Minibio TLDR version]]

# Projetos atuais em andamento

Os projetos atuais registrados neste Vault

```dataview
table Deadline, Status, tags
from #project and !"4 - Archived" and !"Templates"
sort Deadline asc
```


# Last Touched Notes

All the [[Daily Notes|Daily Notes]] are available
```dataview
LIST
WHERE file.cday.weekyear >= date(today).weekyear
	AND file.cday.year = date(today).year
SORT file.cday DESC
```
---

# Livros Últimos Referenciados

Todos os livros estão linkados em [[Livros|Livros]]

```dataview
List
from #books 
WHERE file.cday > (date(today) - dur("3 week"))
```


# Backlog de próximos livros

Pode ser que nunca leia, mas essa lista é a que sigo para adicionar na compra

```add-summary
tags: #toread
```

---

## Projetos Finalizados

```dataview
table Deadline, Status, tags
from #project and "4 - Archived" and !"Templates"
sort Deadline asc
```
