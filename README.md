

# XRP Seed Recovery Tool

A multiprocessing open-source Python utility for recovering and validating 12-word BIP39 seed phrases associated with XRP Ledger classic addresses locally using the standard derivation path "m/44'/144'/0'/0/0". The tool is intended for legitimate wallet recovery, testing, and educational use. It operates on candidate phrases supplied by the user.

## Features

The program provides local tools for these BIP-39 12 word mnemonic seed phrase operations:

1. Testing replacement words in selected positions by replaceing 1–5 positions marked `?` and match an XRP classic address. Use case is when the address and at least 7 words and their positions are known.

2. Search for XRP addresses ending with a specific pattern. Such as the last six of a target "r" address. Use case is similar to mode 1. The difference is when only partial address is known.

3. Replace 1-5 missing words represented as "?" and print only valid BIP-39 12 word seed phrases compatible with XRP addresses as "missing_words.txt". Use case is when we want to save all possible valid 12 word mnemonic seed phrases to a .txt file for further processing.

4. Validate a 12 word seed phrase and derive its XRP address with the derivation path "m/44'/144'/0'/0/0".

5. Display the XRP address for a valid 12 word seed phrase. 

6. Permute 12 supplied words and match a provided address using only the valid BIP-39 phrases derived from the derivation path "m/44'/144'/0'/0/0". Saved to 'descrambled.txt'. Use when all 12 words are correct but in the wrong positions. A known address is needed.

7. Generate a new valid 12 word seed phrase and address using derivation path "m/44'/144'/0'/0/0".

8. Search a fixed-position and/or an unanchored tokenlist.txt for a target address. Uses a btcrecover compatible tokenlist.txt to search for a target address.

9. Automatically tests 1-4 possible incorrect words in any position against a target "r" address. Use case is when at least 8 words are correct but are unsure of their correct position.

#LIMITATIONS

1. 12 word seed phrases only.
2. `m/44'/144'/0'/0/0` only.
3. CPU only
4. These operations are computationally intensive. The highest logical core count and highest base/boost clock speed that can be afforded. See benchmarks.md
5. Modes 1–4, 8, and 9 use multiprocessing; mode 6 scans permutations in a single process.  6. The terminal shows progress, speed and ETA. Mode 6 does not.
7. Four unknown wrong words in mode 9 can require an impractically long exhaustive search as well as 5 missing in mode 1.

## Requirements ##

- Linux, Windows, or macOS
- Python 3.12.10 (3.13 has issues)
- A 64-bit Python installation
- Required Python packages used by the script

Check your Python version:

```bash
python3 --version
```

It is recommended to use a Python virtual environment.

## Installation ##

Clone the repository:

```bash
git clone https://github.com/duhghee/xrprecover.git
cd xrprecover
```

Create a virtual environment:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

On Windows, activate it with:

```powershell
.venv\Scripts\activate
```

Install the dependencies:

```bash
python3 -m pip install -r requirements.txt
```

## Running the Program ##

Display command-line options:

```bash
python3 xrprecover.py --help
```

Start with the default settings:

```bash
python3 xrprecover.py
```

Run with a selected number of processes:

```bash
python3 xrprecover.py --processes 16
```

Run with a selected process count and batch size:

```bash
python3 xrprecover.py --processes 32 --batch-size 2048
```

Only use an option if it appears in the output of:

```bash
python3 xrprecover.py --help
```

## CPU Tuning ##

A reasonable starting point is:

```bash
python3 xrprecover.py --processes 16 --batch-size 2048
```

Increase the process count gradually while monitoring CPU temperature, memory usage, and candidates per second.

The best setting is the one that produces the highest sustained search speed—not necessarily the largest process count.

## Missing Words ##

Enter a question mark (?) at each unknown position when supported by the selected mode.

Example:

```text
word1 word2 ? word4 word5 ? word7 word8 word9 word10 word11 word12
```

Mode 1 replaces only marked positions. Mode 9 tests twelve supplied BIP39 words and determines which 1-4 words may be wrong; it does not use `?`.

## Token Lists ##

Token-list mode uses candidate groups assigned to seed positions. Unanchored positions should exchange candidates only with other unanchored positions. I recommend duhghee/BTCRecover-Tokenlist-Creator


# Acknowledgements

***  gurnec/btcrecover  ***

***  3rdIteration/btcrecover  ***

***  d31337m3/seedy  ***






