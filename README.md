# Relatório AstraZeneca (HTML)

Abrir `index.html` no browser (duplo clique). Funciona offline; as imagens estão em `assets/`.

- Botão **Review notes** (canto superior direito): mostra/esconde as caixas vermelhas com o que o grupo tem de decidir ou corrigir.
- Botão **Theme**: claro/escuro. **Ctrl+P** gera PDF (as notas de revisão não saem na impressão).
- As citações `{AR|p. 27}` no código viram `[1, p. 27]` automaticamente, numeradas por ordem de primeira citação (IEEE). A lista de referências está em `src/05-tail.html`.

## Editar

O ficheiro final é a junção de `src/`. Depois de editar uma parte:

```bash
cd Relatorio && cat src/01-head.html src/02-intro.html src/03-org.html src/04-planning.html src/05-tail.html > index.html
```

- `src/02-intro.html`: Introdução e ODS (NB)
- `src/03-org.html`: Organização e organograma (DC)
- `src/04-planning.html`: Planeamento, SWOT e estratégia (JC); secções 3.1 e 3.2 (SN) estão marcadas como *Pending*; secções 3.4 a 9 como *Next delivery*

A análise detalhada de cada pasta, com páginas do relatório anual, está em `../_analise/`.
