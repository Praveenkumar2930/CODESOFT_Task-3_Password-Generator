# Password Generator

## Overview

This Python script generates secure and random passwords based on user-defined criteria. It allows the user to specify the desired length of the password and whether to include uppercase letters, lowercase letters, numbers, and special characters.

## Features

- Generate passwords of a specified length
- Option to include:
  - Uppercase letters (A-Z)
  - Lowercase letters (a-z)
  - Numbers (0-9)
  - Special characters (!@#$%^&*()-_=+[]{}|;:',.<>?/)

## Requirements

- Python 3.x

## Usage

1. **Clone the repository or download the script**:

   ```bash
  https://github.com/Praveenkumar2930?tab=repositories
   ```

2. **Run the script**:

   ```bash
   python password_generator.py
   ```

3. **Follow the prompts** to generate a password based on your preferences.

## Example

```python
# Sample execution
$ python password_generator.py
Enter the desired length of the password: 12
Include uppercase letters? (yes/no): yes
Include lowercase letters? (yes/no): yes
Include numbers? (yes/no): yes
Include special characters? (yes/no): yes

Generated password: g7#A1t!Wq5m@
```

## Script Details

Here is the main script (`password_generator.py`):

```python
import random
import string

def generate_password(length, use_uppercase, use_lowercase, use_numbers, use_special):
    character_pool = ''
    if use_uppercase:
        character_pool += string.ascii_uppercase
    if use_lowercase:
        character_pool += string.ascii_lowercase
    if use_numbers:
        character_pool += string.digits
    if use_special:
        character_pool += string.punctuation
    
    if not character_pool:
        raise ValueError("At least one character type must be selected")
    
    password = ''.join(random.choice(character_pool) for _ in range(length))
    return password

if __name__ == "__main__":
    length = int(input("Enter the desired length of the password: "))
    use_uppercase = input("Include uppercase letters? (yes/no): ").lower() == 'yes'
    use_lowercase = input("Include lowercase letters? (yes/no): ").lower() == 'yes'
    use_numbers = input("Include numbers? (yes/no): ").lower() == 'yes'
    use_special = input("Include special characters? (yes/no): ").lower() == 'yes'
    
    try:
        password = generate_password(length, use_uppercase, use_lowercase, use_numbers, use_special)
        print("Generated password:", password)
    except ValueError as e:
        print("Error:", e)
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Contributing

Contributions are welcome! Please fork the repository and create a pull request with your changes.

## Contact

For any questions or suggestions, please open an issue or contact [your-email@praveenkumaru101@gmail.com](mailto:your-praveenkumaru101@gmail.com).
