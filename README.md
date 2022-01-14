# GitHub Action for Soteria
This action enables you to run the Solana smart contract vulnerability scanning tool Soteria as part of your CI/CD pipeline.

The action takes the following inputs, but note that they are not required. 
If this is new to you, just run the action without passing any arguments!
```
solanaVersion (default: 1.9.4) - Check Solana releases if needed
option (default: -analyseAll) - Runs the tool against all contracts
buildCommand (default: .) - Targets the bpfel folder
neverFail (default: 1) - Default fails if vulnerabilities are detected
```

You can use this action as part of your project by creating an Action as follows:
```
name: Soteria Scan
on:
  push:
    branches: main
  pull_request:
    branches: main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2
      - name: Soteria Scan
        uses: silas-x/soteria-action@main
        with:
          solanaVersion: "1.9.4"
          options: "-analyzeAll"
          buildCommand: "."
          neverFail: "1"
 ```
 
 Note: I am not the author of Soteria. I can't answer support questions related to the tool and I take no responsibility of the accuracy of it, 
 or the outcomes of running this action. You should not solely rely on the the results of running this tool, as no tool will be able to
 provide assurance of security or completeness of a smart contract.
