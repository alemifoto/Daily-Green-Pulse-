name: Daily Commit

on:
  schedule:
    - cron: '0 11 * * *'

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v2

      - name: Create a dummy commit
        run: |
          date >> dummy.txt
          git config --global user.name 'alemifoto'
          git config --global user.email 'alemifoto282@gmail.com'
          git add dummy.txt
          git commit -m "Daily update"
          git push
