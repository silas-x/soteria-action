# GitHub Action for Soteria
This action enables you to run the Solana smart contract vulnerability scanning tool Soteria as part of your CI/CD pipeline.

## Action inputs :ballot_box:
The action takes the following inputs, but note that they are not required. 
If this is new to you, just run the action without passing any arguments!
```
solanaVersion (default: 1.9.4)        - Check Solana releases if needed
runMode       (default: -analyseAll)  - Runs the tool against all contracts
cargoCom      (default: .)            - Shortcut Cargo build command
neverFail     (default: false)        - Set to true if you don't want to fail a job
```

## Running the Action in GitHub CI :infinity:
You can use this Action as part of your project by creating an Action as follows:
```
name: Soteria Scan
# Update this to match your branch names and requirements
on:
  push:
    branches: main
  pull_request:
    branches: main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Check-out the repository
        uses: actions/checkout@v2
      - name: Soteria Scan
        uses: silas-x/soteria-action@v1
        with:                    # remove if not passing arguments below
          solanaVersion: "1.9.4" # not required
          runMode: "-analyzeAll" # not required
          cargoCom: "."          # not required
          neverFail: "false"     # not required
 ```
 
 ## Managing false positives :space_invader:
 The tool may identify potential issues that you accept as they are to e.g. save compute cycles, or genuine false positives.
 Ignores can be configured by adding a file name coderrect.json in the root folder of the repository you are scanning,
 and in json format, configure your ignores. They can be based on line number, variable or function as shown below:
 ```
 // Example coderrect.json file located in the root folder
 {
  "ignoreRacesAtLocations": [
        "fileNameA.rs:123",
        "fileNameB.rs:321"
    ],
  "ignoreRaceVariables": [
        "var"
    ],
  "ignoreRacesInFunctions": [
        "fn"
    ]
 }
 ```
 ## Feedback :fist_right::fist_left:
 Please raise an issue for suggestions and any bugs related to the Action.
 
 If you feel this Action has helped your project, donations are welcome to this SOL address: _Db4eiNsEXQ5gUZsxGWchj39CXQZ1ZGuuaS4MdSobVhtT_
 
 Made with :heart: by silas

 ## Responsibility :call_me_hand:
 I am not the author of Soteria. I can't answer support questions related to the tool and I take no responsibility of the accuracy of it, 
 or the outcomes of running this action. You should not solely rely on the the results of running this tool, as no tool will be able to
 provide assurance of security or completeness of a smart contract. Use at own risk and see licence note for further information.

