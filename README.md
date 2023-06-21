# Tokeer

Tokeer, a token verification tool that implements the component-configurable transfer model and oracles with datalog technique to identify rug pull risks in the token contracts.

## Project Structure

Introduction of some files and directories

- `README.md`: basic information about the project
- `dataset`: the full dataset and sampling dataset used in our evaluation
- `logic`: datalog files for analyzing the tokens
- `result.json`: the list of outputs of the analysis
- `src`: the source code for decompilation
- `tokeer.py`: the script for running Tokeer

## Instruction

### STEP1: Obtaining Contract Bytecode

Tokeer conducts analysis on the runtime bytecode of the contract. 

To generate it from the Solidity source code, run the following command:

```
solc --bin-runtime contract.sol --overwrite -o ./
```

This will compile the contract and generate the runtime bytecode in the same directory. The output file will have the same name as the contract name with the `.bin-runtime` file extension. 

### STEP2: Analyzing

After obtaining the Solidity bytecode, navigate to the project directory and run the following command to execute the script:

```
python3 ./tokeer.py -C logic/Tokeer.dl path/to/contract.bin-runtime
```

You can also specify the analysing time using the `-T` argument:

```
python3 ./tokeer.py -T 1000 -C logic/Tokeer.dl path/to/contract.hex
```

You can apply `-h` to get more argument instructions.
