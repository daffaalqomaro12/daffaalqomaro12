# 💫 About Me:
I'm currently studying on Electronic Engineering Polytechnic Institute of Surabaya


## 🌐 Socials:
[![Facebook](https://img.shields.io/badge/Facebook-%231877F2.svg?logo=Facebook&logoColor=white)](https://facebook.com/DaffaAlQomaro) [![Instagram](https://img.shields.io/badge/Instagram-%23E4405F.svg?logo=Instagram&logoColor=white)](https://instagram.com/daffaalq_) [![email](https://img.shields.io/badge/Email-D14836?logo=gmail&logoColor=white)](mailto:daffaalqomaro123@gmail.com) 

# 💻 Tech Stack:
![Unity](https://img.shields.io/badge/unity-%23000000.svg?style=flat-square&logo=unity&logoColor=white) ![Itch.io](https://img.shields.io/badge/Itch-%23FF0B34.svg?style=flat-square&logo=Itch.io&logoColor=white) ![Steam](https://img.shields.io/badge/steam-%23000000.svg?style=flat-square&logo=steam&logoColor=white) ![Epic Games](https://img.shields.io/badge/epicgames-%23313131.svg?style=flat-square&logo=epicgames&logoColor=white) ![Notion](https://img.shields.io/badge/Notion-%23000000.svg?style=flat-square&logo=notion&logoColor=white) ![Xbox](https://img.shields.io/badge/xbox-%23107C10.svg?style=flat-square&logo=xbox&logoColor=white)
# 📊 GitHub Stats:
![](https://github-readme-stats.vercel.app/api?username=daffaalqomaro12&theme=catppuccin_mocha&hide_border=false&include_all_commits=false&count_private=false)<br/>
![](https://nirzak-streak-stats.vercel.app/?user=daffaalqomaro12&theme=catppuccin_mocha&hide_border=false)<br/>
![](https://github-readme-stats.vercel.app/api/top-langs/?username=daffaalqomaro12&theme=catppuccin_mocha&hide_border=false&include_all_commits=false&count_private=false&layout=compact)

## 🏆 GitHub Trophies
![](https://github-profile-trophy.vercel.app/?username=daffaalqomaro12&theme=catppuccin_mocha&no-frame=false&no-bg=true&margin-w=4)

### ✍️ Random Dev Quote
![](https://quotes-github-readme.vercel.app/api?type=vetical&theme=tokyonight)

---
[![](https://visitcount.itsvg.in/api?id=daffaalqomaro12&icon=0&color=0)](https://visitcount.itsvg.in)

name: GitHub Snake Game

on:
  # Schedule the workflow to run daily at midnight UTC
  schedule:
    - cron: "0 0 * * *"
  # Allow manual triggering of the workflow
  workflow_dispatch:
  # Trigger the workflow on pushes to the main branch
  push:
    branches:
      - main
jobs:
  generate:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    steps:
      # Step 1: Checkout the repository
      - name: Checkout Repository
        uses: actions/checkout@v3
      # Step 2: Generate the snake animations
      - name: Generate GitHub Contributions Snake Animations
        uses: Platane/snk@v3
        with:
          # GitHub username to generate the animation for
          github_user_name: ${{ github.repository_owner }}
          # Define the output files and their configurations
          outputs: |
            dist/github-snake.svg
            dist/github-snake-dark.svg?palette=github-dark
            dist/ocean.gif?color_snake=orange&color_dots=#bfd6f6,#8dbdff,#64a1f4,#4b91f1,#3c7dd9
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      # Step 3: Deploy the generated files to the 'output' branch
      - name: Deploy to Output Branch
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
          publish_branch: output
          # Optionally, you can set a custom commit message
          commit_message: "Update snake animation [skip ci]"
