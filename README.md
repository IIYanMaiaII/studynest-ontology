# Ontologia Studynest

Ontologia OWL para o sistema Studynest, uma plataforma mobile de colaboração acadêmica que permite a estudantes se organizarem em grupos de estudo, compartilharem materiais e trocarem mensagens.

## Informações Gerais

- **URI**: `http://purl.org/studynest#`
- **Versão**: 1.0.0
- **Licença**: [CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/)
- **Autores**: Yan Oliveira Maia

## Arquivos

- [`studynest.ttl`](studynest.ttl) - Ontologia principal no formato Turtle
- [`index.html`](index.html) - Documentação gerada com pyLODE

## Visão Geral das Classes

| Classe | Descrição |
|--------|-----------|
| `Usuario` | Usuário do sistema |
| `Instituicao` | Instituição de ensino |
| `Disciplina` | Disciplina acadêmica |
| `GrupoEstudo` | Grupo de estudo |
| `MaterialEstudo` | Material compartilhado |
| `Mensagem` | Mensagem em chat |

## 🔗 Principais Relacionamentos

- `Usuario` -[:inscritoEm]-> `Disciplina`
- `Usuario` -[:membroDe]-> `GrupoEstudo`
- `Usuario` -[:publica]-> `MaterialEstudo`
- `Usuario` -[:envia]-> `Mensagem`
- `GrupoEstudo` -[:associadoADisciplina]-> `Disciplina`
- `MaterialEstudo` -[:pertenceADisciplina]-> `Disciplina`
- `Mensagem` -[:pertenceAGrupo]-> `GrupoEstudo`

## Exemplo de Instâncias

### Usuários
- `:JoaoSilva` - Aluno de Cálculo I, administrador do GrupoCalculo
- `:MariaSantos` - Aluna de Cálculo I, membro do GrupoCalculo
- `:PedroOliveira` - Aluno de Programação, administrador do GrupoPOO

### Disciplinas
- `:Matematica` - "Cálculo I" (Área: Exatas)
- `:Programacao` - "Programação Orientada a Objetos" (Área: Tecnologia)

### Grupos
- `:GrupoCalculo` - Grupo para exercícios de Cálculo I
- `:GrupoPOO` - Grupo para projeto final de POO

### Materiais
- `:MaterialLimites` - Lista de exercícios (PDF) publicado por João
- `:MaterialClasses` - Vídeo aula sobre Classes em Java publicado por Pedro

## Exemplo de Consulta SPARQL

### Listar todos os usuários e seus dados básicos

```sparql
PREFIX : <http://purl.org/studynest#>
SELECT ?usuario ?nome ?email ?genero
WHERE {
  ?usuario a :Usuario .
  ?usuario :nome ?nome .
  ?usuario :email ?email .
  ?usuario :genero ?genero .
}
ORDER BY ?nome
