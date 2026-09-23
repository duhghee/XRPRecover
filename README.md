# XRP Seed Recovery Tool

A multiprocessing Python utility for recovering and validating 12-word BIP39 seed phrases associated with XRP Ledger classic addresses.

## Important Warning

Use this program only with wallets that you own or are explicitly authorized to recover.

Never upload or share any of the following:

- Real seed phrases
- Private keys
- Wallet recovery files
- Token lists containing actual seed words
- XRP addresses you consider private
- Search results or saved recovery progress containing sensitive information

For maximum security, run the program on an offline computer.

## Features

The program provides these 12-word BIP-39 operations:

1. Replace 1–5 positions marked `?` and match an XRP classic address.
2. Search for XRP addresses ending with a supplied pattern.
3. Fill missing words and print valid BIP-39 phrases.
4. Validate a seed phrase and display its XRP address.
5. Display the XRP address for a valid phrase.
6. Permute 12 supplied words and print valid BIP-39 phrases.
7. Generate a new seed phrase and address.
8. Search a fixed-position and unanchored tokenlist for a target address.
9. Replace words at any 1–4 positions to match a target XRP address.

Address derivation uses `m/44'/144'/0'/0/0`. Modes 1–4, 8, and 9 use multiprocessing; mode 6 scans permutations in one process. The terminal shows progress and speed. Four unknown wrong words in mode 9 can require an impractically long exhaustive search.

## Requirements

- Linux, Windows, or macOS
- Python 3
- A 64-bit Python installation
- Required Python packages used by the script

Check your Python version:

```bash
python3 --version
```

It is recommended to use a Python virtual environment.

## Installation

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

## Running the Program

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

## CPU Tuning

A reasonable starting point is:

```bash
python3 xrprecover.py --processes 16 --batch-size 2048
```

Increase the process count gradually while monitoring CPU temperature, memory usage, and candidates per second.

The best setting is the one that produces the highest sustained search speed—not necessarily the largest process count.

## Missing Words

Enter a question mark (?) at each unknown position when supported by the selected mode.

Example:

```text
word1 word2 ? word4 word5 ? word7 word8 word9 word10 word11 word12
```

Mode 1 replaces only marked positions. Mode 9 takes twelve supplied BIP-39 words and tests which one to four positions may be wrong; it does not use `?`.

## Token Lists

Token-list mode uses candidate groups assigned to seed positions. Unanchored positions should exchange candidates only with other unanchored positions.

Do not publish a token list containing a genuine or partially reconstructed seed phrase.

***  Inspired by https://github.com/d31337m3/seedy/  ***



