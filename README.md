# GitHub Action for Soteria
This action enables you to run the Solana smart contract vulnerability scanning tool, Soteria, as part of your GitHub CI pipeline in the simplest possible way. There are many ways you can optimise the job, but this action aims to make things super easy!

## Action inputs :ballot_box:
The action takes the following inputs, but note that they are **not** required. 
If this is new to you, just run the action without passing any arguments!
```
solana-version (default: "1.9.14")       - Check Solana releases if needed (https://github.com/solana-labs/solana/releases)
run-mode       (default: "-analyseAll")  - Runs the tool against all programs
cargo-com      (default: ".")            - Shortcut for build command
program-path   (default: ".")            - Add path to a specific program / path
```

## Running the Action in GitHub CI :infinity:
You can use this Action as part of your project by creating an Action as follows:
```
name: Soteria Audit
                                           # Update to match your branch names and requirements
on:
  push:
    branches: main
  pull_request:
    branches: main

jobs:
  audit:
    runs-on: ubuntu-latest
    steps:
      - name: Check-out the repository
        uses: actions/checkout@v2
      - name: Soteria Audit
        continue-on-error: false          # set to true if you don't want to fail jobs
        uses: silas-x/soteria-action@main
        with:                             # remove if not passing arguments below
          solana-version: "1.9.14"        # not required
          run-mode: "-analyzeAll"         # not required
          cargo-com: "."                  # not required
          program-path: "."               # not required
 ```
 
 ## Managing false positives :space_invader:
 The tool may identify potential issues that you accept as they are to e.g. save compute cycles, or genuine false positives.
 Ignores can be configured by adding the below annotation to the line above the line you are wanting to ignore:
 ```
//#[soteria(ignore)]
 ```
 
 ## Feedback :fist_right::fist_left:
 Please raise an issue for suggestions and any bugs related to the Action.
 
 If you feel this Action has helped securing your project and its user's funds, donations are welcome to this SOL address: _Db4eiNsEXQ5gUZsxGWchj39CXQZ1ZGuuaS4MdSobVhtT_

 ## Responsibility :call_me_hand:
 I am not the author of the Soteria tool. I can't answer support questions related to the tool, but I may be able to help connecting you.
 I take no responsibility of the accuracy of it, or the outcomes of running this Action. You should not solely rely on the the results of running this
 tool, as no tool will be able to provide assurance of security or completeness of a smart contract. 
 Use at own risk and engage experts to peer review/formally audit your production contracts.

