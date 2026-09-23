# XRP Seed Recovery Tool

A local, open-source Python utility for recovering and validating **your own** 12-word BIP39 seed phrases associated with XRP Ledger classic addresses.

The tool is intended for legitimate wallet recovery, testing, and educational use. It operates on candidate phrases supplied by the user and derives XRP addresses locally using the standard derivation path:

```text
m/44'/144'/0'/0/0
```

## Intended Use

Use XRPRecover only when:

- You own the wallet or have explicit authorization from the owner.
- You are recovering a seed phrase from your own records or backups.
- You are conducting authorized development, testing, or educational research.

You are solely responsible for ensuring that your use complies with applicable laws, regulations, and third-party terms.

## Security and Privacy

This tool is designed to run locally. For maximum privacy and safety:

- Run it on a trusted, preferably offline computer.
- Never enter a seed phrase into a website, chat, form, or third-party service.
- Do not upload seed phrases, private keys, token lists, recovery files, logs, or search results.
- Treat all generated output and saved progress files as sensitive wallet information.
- Review the source code and dependencies before using the tool with valuable funds.
- Test the workflow with a disposable or empty wallet before attempting recovery of a funded wallet.

**Do not use real wallet secrets in screenshots, bug reports, demonstrations, or public issues.**

## Important Disclaimer

XRPRecover is provided for lawful, authorized wallet recovery and educational purposes only. It is not a custodial service, wallet provider, exchange, or key-storage system.

The software does not guarantee that a missing seed phrase can be recovered, that a derived address is correct for every wallet configuration, or that the program is free from defects. Users must independently verify results and remain responsible for protecting their own credentials and assets.

The authors and contributors are not responsible for:

- Loss of funds or access to a wallet
- Disclosure or compromise of seed phrases or private keys
- Damage caused by misuse, incorrect configuration, or untrusted environments
- Unauthorized access to wallets or accounts
- Any legal or regulatory consequences arising from use of the software

By using this project, you acknowledge that you are using it at your own risk and only for wallets and data you are authorized to access.

## Features

The program provides local tools for:

1. Testing replacement words in selected positions.
2. Searching for XRP addresses matching a supplied pattern.
3. Filling missing words and validating BIP39 phrases.
4. Validating a seed phrase and deriving its XRP address.
5. Deriving an XRP address from a valid phrase.
6. Permuting supplied words and checking BIP39 validity.
7. Generating a new seed phrase and address.
8. Searching authorized candidate token lists.
9. Testing possible incorrect words against a target address.

These operations may be computationally intensive. Use reasonable process and batch settings, and monitor system temperature, memory usage, and power consumption.

## Responsible Disclosure

Please do not include seed phrases, private keys, funded addresses, token lists, recovery files, or other sensitive wallet data in issues or pull requests. For security concerns, describe the problem using sanitized examples and omit all secrets.
