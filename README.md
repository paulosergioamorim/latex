# Template LaTeX

Template para desenvolvimento local de documentos LaTeX no Arch Linux e em sistemas baseados em Debian.

## Dependências

Arch Linux:

```bash
sudo pacman -S --needed texlive make
```

O grupo `texlive` já inclui `pdflatex`, `bibtex` e `latexmk`.

Debian, Ubuntu e derivados (apt):

```bash
sudo apt update
sudo apt install texlive-latex-recommended texlive-latex-extra texlive-fonts-recommended texlive-bibtex-extra latexmk make
```

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

Hifenização em português exige um pacote de idioma extra.

Arch Linux:

```bash
sudo pacman -S texlive-langportuguese
```

Debian, Ubuntu e derivados:

```bash
sudo apt install texlive-lang-portuguese
```

Depois adicione `\usepackage[brazilian]{babel}` em `preamble.tex`.

## CI

O workflow roda apenas ao subir uma tag cujo commit esteja na `main`. Ele
compila `main.tex` com a action `xu-cheng/latex-action` e cria uma release com
o título "Artefato" e o `main.pdf` anexado:

```bash
git tag v1.0.0
git push origin v1.0.0
```
