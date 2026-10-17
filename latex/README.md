# Relatório AstraZeneca — projeto LaTeX

Documento tipografado em LaTeX. O HTML em `../` foi a versão de trabalho;
este projeto é o que dá origem ao entregável.

## Compilar

Na pasta `latex/`:

```bash
tectonic -X compile main.tex
```

O resultado é `main.pdf`. Mantém-no aberto no Preview do macOS: a janela
actualiza-se sozinha a cada compilação.

O preâmbulo deteta o motor com `iftex`, por isso também compila com `pdflatex`,
`xelatex` ou `lualatex` numa instalação TeX Live normal, e no Overleaf sem
configurar o compilador. A bibliografia é BibTeX e resolve-se na segunda
passagem, que o `tectonic` faz sozinho.

## Estrutura

| Ficheiro | O que é |
|---|---|
| `main.tex` | Preâmbulo, folha de rosto, índice e `\input` dos capítulos |
| `secoes/01-introducao.tex` | Capítulo 1 — apresentação da organização e ODS |
| `secoes/02-organizacao.tex` | Capítulo 2 — organograma e análise da estrutura |
| `secoes/03-planeamento.tex` | Capítulo 3 — valores, objetivos, SWOT e estratégia |
| `refs.bib` | As 14 referências, em BibTeX |
| `figuras/` | Só duas imagens: o logo do ISEP e o mapa do relatório anual |

## Convenções

**Citações.** `\cite[p.~27]{AR}` dá `[1, p. 27]`. Chaves: `AR`, `F20`, `INT`,
`ORG`, `PLAN`, `NATURE`, `FOREST`, `LEAD`, `EU`, `MULLARD`, `USP`, `P50`,
`FEIN`, `IQVIA`.

**Tabelas.** `xltabular` com `booktabs`, para partirem entre páginas com o
cabeçalho repetido. Não escrever o número na legenda — o LaTeX numera.

**Badges.** `\bgood{Strength}`, `\bwarn{Moderate}`, `\bbad{Threat}`,
`\bneut{Parity}`. Usam-se para classificações curtas; o verde é favorável, o
âmbar condicional, o vermelho desfavorável, o cinzento neutro.

**Barras.** `\barra{0.75}` e `\barrab{0.75}` desenham uma barra proporcional ao
valor, entre 0 e 1. São `\rule`, não imagens.

**Caixas.** `\begin{analysis}` para interpretação dos autores e
`\begin{sourceslimit}` para os limites das fontes. O rótulo é automático e as
caixas não partem entre páginas.

**Colunas.** `Y` é elástica à esquerda, `R` elástica à direita, `N{2.5cm}` é
estreita e **não hifeniza** — usa-se na primeira coluna das tabelas.

## Três armadilhas já encontradas

1. **Cabeçalho de tabela sozinho no fim da página.** A legenda e os títulos são
   linhas distintas e o `longtable` quebra entre elas. Todas as linhas de
   cabeçalho e de grupo levam `\\*`, que proíbe a quebra.
2. **`\needspace` só onde é mesmo preciso.** Aplicado a todas as tabelas, cria
   um fragmento vazio nas tabelas longas e desperdiça uma página inteira. Está
   usado numa só, a da cadeia de valor, onde a primeira linha não cabia.
3. **Unicode fora do T1.** Setas, travessões, aspas curvas e o sinal de menos
   rebentam com `pdflatex`. Estão todos escritos com comandos LaTeX.
