name: main

on:
  push:
    branches:
      - main
  schedule:
    - cron: "* */6 * * *"
permissions:
  contents: write
jobs:
  autogreen:
    runs-on: ubuntu-latest
    steps:
      - name: Clone repository
        uses: actions/checkout@v2

      - name: stick
        run: |
          date > date.txt
          git config --local user.name "alemifoto"
          git config --local user.email "alemifoto282@gmail.com"
          git add date.txt
          git commit --allow-empty -m "updated txt"
          git push  
