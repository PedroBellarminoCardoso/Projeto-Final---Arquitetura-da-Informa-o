# Proposta de Refatoração de Taxonomia

## 1) Objetivo
Padronizar a estrutura do repositório para um formato profissional, portável e amigável ao Git/GitHub, reduzindo riscos de erro com nomes de arquivos e melhorando manutenção, versionamento e colaboração.

## 2) Diagnóstico da Estrutura Atual

### Problemas identificados
- Uso de acentos, cedilha, espaços e parênteses em pastas/arquivos (ex.: `Organização (Templates 4 a 5)`).
- Inconsistência de prefixo (`PMH` vs `PHM`) e de separadores (`_`, espaço e `-`).
- Nome da pasta raiz com ruído de formatação (`Projeto-Final---Arquitetura-da-Informa-o`).
- Uso predominante de arquivos binários (`.docx`, `.jpg`), que dificultam diff e histórico no Git.

### Impacto técnico
- Possíveis incompatibilidades entre sistemas operacionais e ferramentas de CI/CD.
- URLs e paths menos legíveis no GitHub.
- Maior chance de erro em links internos e scripts.
- Menor rastreabilidade de mudanças por causa de arquivos binários.

## 3) Padrão-Alvo Recomendado

### Convenções de nomenclatura
- Usar **kebab-case**: minúsculas + hífen (`-`).
- Não usar acentos/cedilha/caracteres especiais.
- Evitar espaços e parênteses em nomes.
- Padronizar prefixo único: **`pmh-`** (ou `phm-`, mas apenas um).
- Ordenar por sequência lógica com numeração (`01`, `02`, `03`...).

### Formatos de arquivo
- Preferir texto versionável: `.md` para conteúdo textual.
- Para tabelas/inventário: `.csv` ou tabela em Markdown.
- Se houver exigência acadêmica de formato final: anexar `.pdf` de entrega.
- Manter `.docx` apenas como artefato transitório de edição local.

## 4) Estrutura Alvo Sugerida

```text
projeto-final-arquitetura-informacao/
├── README.md
├── 01-design-conceitual/
│   ├── pmh-01-briefing.md (ou .pdf)
│   ├── pmh-02-proto-personas.md (ou .pdf)
│   └── pmh-03-top-tarefas.md (ou .pdf)
└── 02-organizacao/
    ├── pmh-04-inventario-conteudo.csv (ou .md/.pdf)
    └── pmh-05-requisitos-informacionais.md (ou .pdf)
```

## 5) Mapeamento de Renomeação (Atual → Proposto)

- `Design Conceitual (Templates 1 a 3)/` → `01-design-conceitual/`
- `Organização (Templates 4 a 5)/` → `02-organizacao/`
- `PMH_Briefing.docx` → `pmh-01-briefing.md` (ou `.pdf`)
- `PMH_Proto-Personas.docx` → `pmh-02-proto-personas.md` (ou `.pdf`)
- `PHM_Top tarefas.docx` → `pmh-03-top-tarefas.md` (corrigir prefixo + padrão)
- `Inventário de Conteúdo.jpg` → `pmh-04-inventario-conteudo.csv` (preferencial) ou `.md/.pdf`
- `Template_05_Requisitos_Informacionais.docx` → `pmh-05-requisitos-informacionais.md` (ou `.pdf`)

## 6) Plano de Migração Seguro

1. **Congelar alterações** durante a reorganização (janela curta).
2. **Criar branch dedicada**: `chore/taxonomy-refactor`.
3. **Renomear pastas e arquivos** conforme mapeamento.
4. **Converter conteúdo** (`.docx`/`.jpg`) para `.md`/`.csv`/`.pdf`.
5. **Atualizar links internos** no `README.md` e documentos.
6. **Validar abertura de arquivos e links** localmente e no GitHub.
7. **Abrir PR com descrição completa** da migração e racional técnico.

## 7) Critérios de Aceite
- Não existem nomes com espaços, acentos, cedilha ou parênteses.
- Todos os arquivos seguem kebab-case.
- Prefixo está consistente (`pmh-`).
- Sequência lógica preservada por numeração.
- Conteúdo principal está em formato versionável (`.md`/`.csv`) e/ou entrega final em `.pdf`.

## 8) Benefícios Esperados
- Repositório mais profissional e escalável.
- Melhor histórico de versionamento e revisão.
- Menos erros de compatibilidade entre ambientes.
- Navegação e manutenção mais simples para toda a equipe.
