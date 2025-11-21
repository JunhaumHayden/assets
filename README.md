<h1 align="center"> Galeria de Imagens <br> <span style="font-size:1.5rem;">🚀 Frontend Assets</span> </h1>

<p align="center">
  <img src="http://img.shields.io/static/v1?label=STATUS&message=Em%20Desenvolvimento&color=brightgreen&style=for-the-badge"/>
</p>

<p align="center">
  <em> <strong>Galeria de Imagens</strong></em>
</p>

---

<div align="center">


[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/license/mit/)
[![Made with Love](https://img.shields.io/badge/Made%20with-💖-red)]()

[![GitHub Repo stars](https://img.shields.io/github/stars/JunhaumHayden/SmartRent?style=social)](https://github.com/JunhaumHayden/SmartRent)
[![GitHub forks](https://img.shields.io/github/forks/JunhaumHayden/SmartRent?style=social)](https://github.com/JunhaumHayden/SmartRent/fork)
[![GitHub watchers](https://img.shields.io/github/watchers/JunhaumHayden/SmartRent?style=social)](https://github.com/JunhaumHayden/SmartRent/watchers)

</div>

---

## Exemplo de Cypher Script para Noe4j de um banco de dados de um web site de streaming

```cypher
// =============================================
// CRIAÇÃO DAS ENTIDADES PRINCIPAIS
// =============================================

// Criar usuários
CREATE (u1:User {id: 'user1', name: 'Alice Silva', email: 'alice@email.com', join_date: date('2023-01-15')})
CREATE (u2:User {id: 'user2', name: 'Bob Santos', email: 'bob@email.com', join_date: date('2023-02-20')})
CREATE (u3:User {id: 'user3', name: 'Carol Oliveira', email: 'carol@email.com', join_date: date('2023-03-10')});

// Criar gêneros
CREATE (g1:Genre {id: 'action', name: 'Ação'})
CREATE (g2:Genre {id: 'drama', name: 'Drama'})
CREATE (g3:Genre {id: 'comedy', name: 'Comédia'})
CREATE (g4:Genre {id: 'sci-fi', name: 'Ficção Científica'})
CREATE (g5:Genre {id: 'thriller', name: 'Thriller'});

// Criar atores
CREATE (a1:Actor {id: 'actor1', name: 'Tom Hanks', birth_year: 1956})
CREATE (a2:Actor {id: 'actor2', name: 'Meryl Streep', birth_year: 1949})
CREATE (a3:Actor {id: 'actor3', name: 'Leonardo DiCaprio', birth_year: 1974})
CREATE (a4:Actor {id: 'actor4', name: 'Scarlett Johansson', birth_year: 1984})
CREATE (a5:Actor {id: 'actor5', name: 'Robert Downey Jr.', birth_year: 1965});

// Criar diretores
CREATE (d1:Director {id: 'director1', name: 'Steven Spielberg', birth_year: 1946})
CREATE (d2:Director {id: 'director2', name: 'Christopher Nolan', birth_year: 1970})
CREATE (d3:Director {id: 'director3', name: 'Quentin Tarantino', birth_year: 1963});

// =============================================
// CRIAÇÃO DE FILMES
// =============================================

CREATE (m1:Movie {
    id: 'movie1',
    title: 'Forrest Gump',
    release_year: 1994,
    duration: 142,
    description: 'A história de um homem simples que testemunha eventos históricos'
})
CREATE (m2:Movie {
    id: 'movie2',
    title: 'Inception',
    release_year: 2010,
    duration: 148,
    description: 'Um ladrão que rouba segredos do subconsciente'
})
CREATE (m3:Movie {
    id: 'movie3',
    title: 'Pulp Fiction',
    release_year: 1994,
    duration: 154,
    description: 'Várias histórias de criminosos em Los Angeles se entrelaçam'
})
CREATE (m4:Movie {
    id: 'movie4',
    title: 'The Avengers',
    release_year: 2012,
    duration: 143,
    description: 'Super-heróis se unem para salvar o mundo'
});

// =============================================
// CRIAÇÃO DE SÉRIES
// =============================================

CREATE (s1:Series {
    id: 'series1',
    title: 'Stranger Things',
    start_year: 2016,
    end_year: 2024,
    seasons: 4,
    description: 'Um grupo de crianças enfrenta forças sobrenaturais'
})
CREATE (s2:Series {
    id: 'series2',
    title: 'The Crown',
    start_year: 2016,
    end_year: 2023,
    seasons: 6,
    description: 'A vida da Rainha Elizabeth II e eventos históricos'
});

// =============================================
// CONEXÕES - RELACIONAMENTOS
// =============================================

// Usuários assistiram conteúdos com avaliações
MATCH (u:User {id: 'user1'}), (m:Movie {id: 'movie1'})
CREATE (u)-[:WATCHED {
    rating: 5,
    watch_date: date('2023-05-10'),
    watch_count: 1
}]->(m);

MATCH (u:User {id: 'user1'}), (m:Movie {id: 'movie2'})
CREATE (u)-[:WATCHED {
    rating: 4,
    watch_date: date('2023-06-15'),
    watch_count: 2
}]->(m);

MATCH (u:User {id: 'user2'}), (m:Movie {id: 'movie3'})
CREATE (u)-[:WATCHED {
    rating: 5,
    watch_date: date('2023-07-20'),
    watch_count: 1
}]->(m);

MATCH (u:User {id: 'user3'}), (s:Series {id: 'series1'})
CREATE (u)-[:WATCHED {
    rating: 4,
    watch_date: date('2023-08-05'),
    watch_count: 1
}]->(s);

// Atores atuaram em filmes
MATCH (a:Actor {id: 'actor1'}), (m:Movie {id: 'movie1'})
CREATE (a)-[:ACTED_IN {character: 'Forrest Gump'}]->(m);

MATCH (a:Actor {id: 'actor3'}), (m:Movie {id: 'movie2'})
CREATE (a)-[:ACTED_IN {character: 'Dom Cobb'}]->(m);

MATCH (a:Actor {id: 'actor4'}), (m:Movie {id: 'movie4'})
CREATE (a)-[:ACTED_IN {character: 'Natasha Romanoff'}]->(m);

MATCH (a:Actor {id: 'actor5'}), (m:Movie {id: 'movie4'})
CREATE (a)-[:ACTED_IN {character: 'Tony Stark'}]->(m);

// Atores atuaram em séries
MATCH (a:Actor {id: 'actor2'}), (s:Series {id: 'series2'})
CREATE (a)-[:ACTED_IN {character: 'Rainha Elizabeth II'}]->(s);

// Diretores dirigiram filmes
MATCH (d:Director {id: 'director1'}), (m:Movie {id: 'movie1'})
CREATE (d)-[:DIRECTED]->(m);

MATCH (d:Director {id: 'director2'}), (m:Movie {id: 'movie2'})
CREATE (d)-[:DIRECTED]->(m);

MATCH (d:Director {id: 'director3'}), (m:Movie {id: 'movie3'})
CREATE (d)-[:DIRECTED]->(m);

// Conteúdos pertencem a gêneros
MATCH (m:Movie {id: 'movie1'}), (g:Genre {id: 'drama'})
CREATE (m)-[:IN_GENRE]->(g);

MATCH (m:Movie {id: 'movie1'}), (g:Genre {id: 'comedy'})
CREATE (m)-[:IN_GENRE]->(g);

MATCH (m:Movie {id: 'movie2'}), (g:Genre {id: 'sci-fi'})
CREATE (m)-[:IN_GENRE]->(g);

MATCH (m:Movie {id: 'movie2'}), (g:Genre {id: 'thriller'})
CREATE (m)-[:IN_GENRE]->(g);

MATCH (m:Movie {id: 'movie3'}), (g:Genre {id: 'thriller'})
CREATE (m)-[:IN_GENRE]->(g);

MATCH (m:Movie {id: 'movie4'}), (g:Genre {id: 'action'})
CREATE (m)-[:IN_GENRE]->(g);

MATCH (s:Series {id: 'series1'}), (g:Genre {id: 'sci-fi'})
CREATE (s)-[:IN_GENRE]->(g);

MATCH (s:Series {id: 'series1'}), (g:Genre {id: 'thriller'})
CREATE (s)-[:IN_GENRE]->(g);

MATCH (s:Series {id: 'series2'}), (g:Genre {id: 'drama'})
CREATE (s)-[:IN_GENRE]->(g);

```

## 📸 Galeria de Imagens

Repositório centralizado para assets do projeto 


[Acesso aqui](https://junhaumhayden.github.io/assets/)


---
### Exemplo

#### 🛰️ Control Server
![Control Server 2025](https://junhaumhayden.github.io/assets/spacelab/control_server_2025-10.png)



## Estrutura do Projeto

```plaintext
assets/
├── spacelab/
│ ├── control_server_2025-10.png
│ └── data_flowchart.png
└── README.md
```
---

##  Licença

MIT — ou seja: use, quebre, refaça, mas me cite se for ficar famoso com isso 😎

---

🧙‍♂️ Autor
<table> <tr>  <td align="center"> <a href="https://github.com/JunhaumHayden"> <img src="https://avatars.githubusercontent.com/u/79289647?v=4" width="115"/><br> <sub><b>Carlos Hayden</b></sub> </a> </td> </tr> </table>
<p align="center"> <em>🧠💻 Built with data, code & caffeine.<br> May the <strong>rent</strong> be ever in your favor.</em> ☕✨ </p>


