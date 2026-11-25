# Password Generator

A simple command-line-friendly password generator written in Python. It builds random passwords from the character types you choose, using Python's `secrets` module so the output is suitable for real security use.

## Features

- Adjustable password length
- Toggle lowercase letters, uppercase letters, digits, and symbols
- Uses `secrets` (cryptographically secure) instead of `random`
- No third-party dependencies

## Requirements

- Python 3.6 or newer (the `secrets` module was added in 3.6)

## Installation

```bash
git clone https://github.com/C3mil9/password-generator.git
cd password-generator
```

## Usage

### Run the script

```bash
python password_gen.py
```

### Use it in your own code

```python
from password_gen import generate_password

# Default: 12 characters, all character types
print(generate_password())

# 20 characters, no symbols
print(generate_password(20, use_symbols=False))

# 16 characters, letters only
print(generate_password(16, use_digits=False, use_symbols=False))
```

### Options

| Parameter     | Type | Default | Description                          |
|---------------|------|---------|--------------------------------------|
| `length`      | int  | `12`    | Number of characters in the password |
| `use_lower`   | bool | `True`  | Include lowercase letters (a-z)      |
| `use_upper`   | bool | `True`  | Include uppercase letters (A-Z)      |
| `use_digits`  | bool | `True`  | Include digits (0-9)                 |
| `use_symbols` | bool | `True`  | Include punctuation symbols          |

If every character type is turned off, the function raises a `ValueError`.

## How it works

1. The enabled character types are combined into one pool of characters.
2. `secrets.choice()` picks one character from the pool, once for each position in the password.
3. The characters are joined into a single string and returned.

The standard `random` module is predictable and should never be used for passwords. `secrets` draws from the operating system's secure random source.

## Roadmap

- [ ] Guarantee at least one character from each enabled type
- [ ] Command-line arguments with `argparse`
- [ ] Exclude look-alike characters (`l`, `1`, `I`, `O`, `0`)
- [ ] Password strength (entropy) estimate
- [ ] Passphrase mode
- [ ] Unit tests with `pytest`

## Security note

Generated passwords are not stored or logged anywhere. Use a reputable password manager to save the passwords you create.

## License

This project is licensed under the MIT License. Add a `LICENSE` file to your repository to match.
