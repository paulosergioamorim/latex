# Template LaTeX

Template para desenvolvimento local de documentos LaTeX no Arch Linux.

## Dependências

```bash
sudo pacman -S --needed texlive make
```

O grupo `texlive` já inclui `pdflatex`, `bibtex` e `latexmk`.

## Uso

```bash
make
```

```bash
make watch
```

```bash
make clean
```

O PDF é gerado em `build/main.pdf`.

## Estrutura

```
main.tex           documento principal
preamble.tex       pacotes e configurações
sections/          uma seção por arquivo
figures/           imagens (já configurado em \graphicspath)
tables/            tabelas
bib/               arquivos .bib
.latexmkrc         configuração do latexmk
.github/workflows/ compilação no GitHub Actions
```

## Português

Hifenização em português exige o pacote `texlive-langportuguese`, que não faz
parte do grupo `texlive`:

```bash
sudo pacman -S texlive-langportuguese
```

Depois adicione `\usepackage[brazilian]{babel}` em `preamble.tex`.

## CI

A cada push o workflow compila `main.tex` com a action `xu-cheng/latex-action`.

No branch `main`, o PDF é publicado na release `latest`, visível na lateral da
página do repositório, com link direto:

https://github.com/paulosergioamorim/latex/releases/latest/download/main.pdf

Nos demais branches, o PDF fica como artefato `main-pdf` na aba Actions.
