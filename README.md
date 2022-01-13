# GitHub Action for Soteria
This action enables you to run the Solana smart contract vulnerability scanning tool Soteria as part of your CI/CD pipeline.

The action takes the following inputs:
```
solanaVersion (default: 1.9.4)
option (detault: -analyseAll)
buildCommand (defalt: .)
```

You can use this action as part of your project by creating an Action as follows:
```
name: Soteria Scan
on:
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2
      - name: Soteria Scan
        uses: silas-x/soteria-action@main
 ```
 
 Note: I am not the author of Soteria. I can't answer support questions related to the tool and I take no responsibility of the accuracy of it, 
 or the outcomes of running this action. You should not solely rely on the the results of running this tool, as no tool will be able to
 provide assurance of security or completeness of a smart contract.
