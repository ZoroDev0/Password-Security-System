# Password Security System

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![MIT License](https://img.shields.io/badge/License-MIT-green.svg)

A comprehensive Python-based password security system featuring intelligent password generation, validation, strength analysis, and security decorators for enterprise-grade password management.

---

## 📋 Table of Contents

- [Features](#-features)
- [System Components](#-system-components)
- [Technologies Used](#-technologies-used)
- [Project Structure](#-project-structure)
- [Installation](#-installation)
- [Usage](#-usage)
- [API Reference](#-api-reference)
- [Configuration](#-configuration)
- [Analytics](#-analytics)
- [Contributing](#-contributing)
- [License](#-license)
- [Contact](#-contact)

---

## ✨ Features

### Core Features
- **Secure Password Generation** - Cryptographically secure password creation using Python's `secrets` module
- **Comprehensive Validation** - Multi-rule password validation engine
- **Strength Analysis** - Real-time password strength scoring (0-100)
- **Security Decorators** - Logging and warning system for sensitive operations
- **Improvement Suggestions** - Actionable recommendations for stronger passwords

### Validation Rules
- ✅ Minimum Length (8+ characters)
- ✅ Uppercase Letters (A-Z)
- ✅ Lowercase Letters (a-z)
- ✅ Numeric Digits (0-9)
- ✅ Special Characters (!@#$%^&*)

### Security Features
- **Strength Indicators** - Visual feedback: Weak, Fair, Good, Strong, Very Strong
- **Customizable Generation** - Configure character types and length
- **Validation History** - Track and analyze password validation attempts
- **Weak Password Database** - Identify commonly used weak passwords
- **Analytics Dashboard** - Jupyter notebook for security analysis

---

## 🔧 System Components

### 1. PasswordGenerator (`PasswordGenerator.py`)
Generates cryptographically secure passwords with customizable options.

**Features:**
- Configurable password length (minimum 8 characters)
- Optional character types: uppercase, lowercase, digits, symbols
- Uses Python's `secrets` module for cryptographic security
- Input validation and error handling

**Usage:**
```python
from PasswordGenerator import PasswordGenerator

# Generate a 16-character password with all character types
generator = PasswordGenerator(length=16)
password = generator.generate()
```

### 2. PasswordValidator (`PasswordValidator.py`)
Validates passwords against security criteria and calculates strength scores.

**Features:**
- 5-point validation rule system
- Strength scoring (0-100)
- Strength labels: Weak, Fair, Good, Strong, Very Strong
- Detailed validation reports

**Usage:**
```python
from PasswordValidator import PasswordValidator

validator = PasswordValidator("MySecureP@ss123")
results = validator.validate()
score = validator.strength_score()
label = validator.strength_label()
```

### 3. SecurityFeatures (`SecurityFeatures.py`)
Provides advanced security analysis and improvement recommendations.

**Features:**
- Real-time strength indicators
- AI-driven improvement suggestions
- Character composition analysis
- Common weakness detection

**Usage:**
```python
from SecurityFeatures import SecurityFeatures

security = SecurityFeatures("password123")
score, label = security.strength_indicator()
suggestions = security.improvement_suggestions()
```

### 4. SecurityManager (`SecurityManager.py`)
Centralized security management and configuration.

**Features:**
- Security policy enforcement
- Logging and audit trails
- Configuration management
- Security event tracking

### 5. SecurityDecorators (`SecurityDecorators.py`)
Decorator functions for securing sensitive operations.

**Features:**
- `@security_warning` - Logs security-sensitive operations
- Error handling and monitoring
- Audit trail support

---

## 🛠 Technologies Used

| Technology | Purpose |
|------------|---------|
| **Python 3.8+** | Core language |
| **secrets** | Cryptographic random generation |
| **re (regex)** | Pattern matching for validation |
| **Jupyter Notebook** | Data analysis and visualization |
| **Pandas** | Data manipulation and analysis |
| **CSV** | Data storage format |

---

## 📁 Project Structure

```
password-security-system/
├── main.py                      # Main application entry point
├── PasswordGenerator.py          # Password generation engine
├── PasswordValidator.py          # Validation logic
├── SecurityFeatures.py           # Advanced security features
├── SecurityManager.py            # Central security manager
├── SecurityDecorators.py         # Security-focused decorators
├── Analytics.ipynb               # Jupyter notebook for analysis
├── validation_history.csv        # Historical validation records
├── weak_passwords.csv            # Common weak passwords database
└── README.md                      # This file
```

---

## 🚀 Installation

### Prerequisites
- Python 3.8 or higher
- pip (Python package manager)
- (Optional) Jupyter Notebook for analytics

### Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/ZoroDev0/Password-Security-System.git
   ```

2. **Navigate to project directory**
   ```bash
   cd password-security-system
   ```

3. **Install dependencies (if required)**
   ```bash
   pip install -r requirements.txt
   ```
   
   Or install individually:
   ```bash
   pip install jupyter pandas
   ```

4. **Run the application**
   ```bash
   python main.py
   ```

---

## 💻 Usage

### Interactive Mode

Simply run the main script:
```bash
python main.py
```

**Workflow:**
1. Enter desired password length (minimum 8, default 12)
2. System generates a secure password
3. Full validation report is displayed
4. Strength score and suggestions provided

**Example Output:**
```
Enter password length (minimum 8, press Enter for default 12): 16

Generated Secure Password: K7@mPqR$xL9nB#2v

Password Validation Report:
Minimum Length (8+): ✓
Uppercase Letter: ✓
Lowercase Letter: ✓
Digit: ✓
Special Character: ✓

Strength Score: 95/100
Strength Indicator: Very Strong

Improvement Suggestions:
→ Consider increasing length to 20+ for maximum security
```

### Programmatic Usage

```python
# Generate and validate a password
from PasswordGenerator import PasswordGenerator
from PasswordValidator import PasswordValidator
from SecurityFeatures import SecurityFeatures

# Step 1: Generate
generator = PasswordGenerator(length=16)
password = generator.generate()

# Step 2: Validate
validator = PasswordValidator(password)
validation_results = validator.validate()
strength_score = validator.strength_score()

# Step 3: Get suggestions
security = SecurityFeatures(password)
score, label = security.strength_indicator()
suggestions = security.improvement_suggestions()

print(f"Password: {password}")
print(f"Score: {strength_score}/100")
print(f"Label: {label}")
```

---

## 🔌 API Reference

### PasswordGenerator

```python
PasswordGenerator(length=12, use_upper=True, use_lower=True, 
                 use_digits=True, use_symbols=True)
```

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `length` | int | 12 | Password length (min: 8) |
| `use_upper` | bool | True | Include uppercase letters |
| `use_lower` | bool | True | Include lowercase letters |
| `use_digits` | bool | True | Include numeric digits |
| `use_symbols` | bool | True | Include special characters |

**Methods:**
- `generate()` - Returns a secure password string

---

### PasswordValidator

```python
PasswordValidator(password: str)
```

**Methods:**
- `validate()` - Returns dict of validation results
- `strength_score()` - Returns score (0-100)
- `strength_label()` - Returns label string
- `has_min_length()` - Boolean check
- `has_uppercase()` - Boolean check
- `has_lowercase()` - Boolean check
- `has_digit()` - Boolean check
- `has_symbol()` - Boolean check

---

### SecurityFeatures

```python
SecurityFeatures(password: str)
```

**Methods:**
- `strength_indicator()` - Returns tuple (score, label)
- `improvement_suggestions()` - Returns list of suggestions
- `analyze_composition()` - Returns character breakdown

---

## ⚙️ Configuration

### Security Policies

Edit security settings in `SecurityManager.py`:

```python
# Minimum password requirements
MIN_LENGTH = 8
REQUIRE_UPPERCASE = True
REQUIRE_LOWERCASE = True
REQUIRE_DIGITS = True
REQUIRE_SYMBOLS = True

# Strength thresholds
WEAK_THRESHOLD = 30
FAIR_THRESHOLD = 50
GOOD_THRESHOLD = 70
STRONG_THRESHOLD = 85
```

### Weak Passwords Database

The `weak_passwords.csv` file contains common weak passwords that are automatically checked. Add entries to expand the database.

---

## 📊 Analytics

### Jupyter Notebook Analysis

Run `Analytics.ipynb` to explore:
- Validation history trends
- Strength distribution analysis
- Common validation failures
- Password generation statistics

**Launch Analytics:**
```bash
jupyter notebook Analytics.ipynb
```

### Data Files

- **validation_history.csv** - Records all validation attempts with timestamps
- **weak_passwords.csv** - Database of commonly used weak passwords

---

## 🤝 Contributing

Contributions are welcome! Here's how to contribute:

1. **Fork the repository**
   ```bash
   git clone https://github.com/ZoroDev0/Password-Security-System.git
   ```

2. **Create a feature branch**
   ```bash
   git checkout -b feature/YourFeature
   ```

3. **Make your changes**
   - Follow PEP 8 style guide
   - Add docstrings to functions
   - Include comments for complex logic

4. **Commit your changes**
   ```bash
   git commit -m 'Add YourFeature'
   ```

5. **Push to the branch**
   ```bash
   git push origin feature/YourFeature
   ```

6. **Open a Pull Request**

---

## 📜 License

This project is licensed under the MIT License - see the LICENSE file for details.

```
MIT License

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

---

## 📞 Contact

**Sasanka (Zoro)** - Your Security Developer

- 🌐 Portfolio: [sasankawrites.in](https://sasankawrites.in/)
- 🔗 LinkedIn: [@zorodev](https://www.linkedin.com/in/zorodev/)
- 📸 Instagram: [@zorodev.exe](https://www.instagram.com/zorodev.exe)
- 💻 GitHub: [@ZoroDev0](https://github.com/ZoroDev0)

### Project Repository
- 📍 GitHub: [Password-Security-System](https://github.com/ZoroDev0/Password-Security-System)
- 📧 Email: Contact via GitHub

---

## 🙏 Acknowledgments

- Python's `secrets` module for cryptographic security
- OWASP for password security guidelines
- Community feedback and contributions

---

## 🔐 Security Notice

This tool is designed for educational and professional use. While it implements security best practices:
- Store generated passwords securely
- Never log passwords in production
- Use alongside professional password managers
- Follow OWASP guidelines for additional security

---

<p align="center">
  Made with 🔐 by <a href="https://github.com/ZoroDev0">Zoro</a>
</p>

<p align="center">
  ⭐ Star this repository if you found it helpful!
</p>
