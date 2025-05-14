<h1 align="left">Olá 👋 Como vai?</h1>

###

<p align="left">Meu nome é Cauã e sou estudante de programação de Belo Horizonte, Brasil.</p>

###

<h2 align="left">About me</h2>

###

<br clear="both">

<img align="right" height="100" src="https://i.pinimg.com/originals/95/c8/ba/95c8bacc7d615b8d678ed0424b0af7a5.gif"  />

###

<p align="left">Atualmente, estou cursando desenvolvimento full stack, onde estou adquirindo experiência em várias tecnologias, incluindo Python, JavaScript, HTML e CSS. Tenho focado no aprendizado de Python, que foi a linguagem com a qual comecei minha jornada na programação. Estou me preparando para iniciar minha carreira no setor de tecnologia, buscando um estágio para aplicar meus conhecimentos e continuar desenvolvendo minhas habilidades em programação e tecnologia da informação.</p>

###

<h2 align="left">I code with</h2>

###

<div align="left">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-plain.svg" height="40" alt="javascript logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" height="40" alt="python logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-plain.svg" height="40" alt="html5 logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-plain.svg" height="40" alt="css3 logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg" height="40" alt="mysql logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/sqlite/sqlite-original.svg" height="40" alt="sqlite logo"  />
</div>

###

<img src="https://raw.githubusercontent.com/cazzubat/cazzubat/output/snake.svg" alt="Snake animation" />

###

name: Generate snake animation

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - main

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: dist/snake.svg?palette=github-dark


      - name: push snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
