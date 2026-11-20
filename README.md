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
.github/workflows/ compilação no GitHub Actions (container archlinux)
```

## Português

Hifenização em português exige o pacote `texlive-langportuguese`, que não faz
parte do grupo `texlive`:

```bash
sudo pacman -S texlive-langportuguese
```

Depois adicione `\usepackage[brazilian]{babel}` em `preamble.tex` e o mesmo
pacote na etapa de instalação do workflow.

## CI

A cada push o workflow compila `main.tex` em um container `archlinux:latest`
e disponibiliza o PDF como artefato `main-pdf` na aba Actions.
