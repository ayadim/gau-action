New project to create gau-action

**Workflow** - `.github/workflows/gau.yml`
**Example**

```yaml

name: 💥 gau - archive crawler
#https://github.com/ayadim/gau-action
on:
    schedule:
      - cron: '0 0 * * *'
    workflow_dispatch:

jobs:
  gau-scan:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-go@v3
        with:
          go-version: 1.17

      - name: 💥 gau - archive crawler
        uses: ayadim/gau-action@main
        with:
          urls: input-data/gau-domains.txt
          threads: 10

      - name: GitHub Workflow artifacts
        uses: actions/upload-artifact@v2
        with:
          name: gau.log
          path: gau.log



```

**include Subdomains**

```yaml 

name: 💥 gau - archive crawler
#https://github.com/ayadim/gau-action
on:
    schedule:
      - cron: '0 0 * * *'
    workflow_dispatch:

jobs:
  gau-scan:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-go@v3
        with:
          go-version: 1.17

      - name: 💥 gau - archive crawler
        uses: ayadim/gau-action@main
        with:
          urls: input-data/gau-domains.txt
          threads: 10
          subdomains: false

      - name: GitHub Workflow artifacts
        uses: actions/upload-artifact@v2
        with:
          name: gau.log
          path: gau.log



```