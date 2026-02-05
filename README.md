<div align="center">

# 🚀 CRUD API Testing with JMeter

[![JMeter Version](https://img.shields.io/badge/JMeter-5.6.3-blue)](https://jmeter.apache.org/)
[![License](https://img.shields.io/badge/License-Apache%202.0-lightgrey)](LICENSE)

</div>

## 📋 Table of Contents
- [Overview](#overview)
- [✨ Features](#features)
- [🚀 Quick Start](#quick-start)
- [📁 File Structure](#file-structure)
- [🎯 Usage Examples](#usage-examples)
- [📊 Expected Results](#expected-results)
- [🔧 Troubleshooting](#troubleshooting)
- [🤝 Contributing](#contributing)
- [📄 License](#license)

## 📖 Overview

**CRUD_API_Complete** is a comprehensive JMeter test plan that executes a **complete CRUD workflow** (Create, Read, Update, Delete) against the public [JSONPlaceholder API](https://jsonplaceholder.typicode.com/users).

This data-driven test validates user management operations with proper assertions and JSON correlation for realistic API testing.

## ✨ Features

- ✅ **Full CRUD Coverage**: POST → GET → PATCH → DELETE → Verification
- 📊 **Data-Driven**: CSV support + dynamic random data generation
- 🧪 **Response Validation**: HTTP status code assertions (201/200)
- 🔗 **JSON Correlation**: Automatic ID extraction for chained requests
- 🎮 **Dual Mode**: GUI mode for debugging + CLI mode for CI/CD
- 📈 **Results Monitoring**: View Results Tree + JTL export

## 🚀 Quick Start

### Prerequisites
- JMeter 5.6.3+ ([Download](https://jmeter.apache.org/download_jmeter.cgi))
- Java 8+
- (Optional) `users.csv` in the same folder as `.jmx`

### 1. Clone Repository
```bash
git clone https://github.com/yourusername/CRUD_API_Complete.git
cd CRUD_API_Complete


### 2. GUI Mode (Recommended for first run)
```bash
jmeter
```
**OR** Open JMeter → File → Open → `CRUD_API_Complete.jmx`
- Click green ▶️ **Start** button
- Check **View Results Tree** listener

### 3. CLI Mode (CI/CD)
```bash
jmeter -n -t CRUD_API_Complete.jmx -l results.jtl
```

## 📁 File Structure
```
CRUD_API_Complete/
├── CRUD_API_Complete.jmx      # Main test plan
├── users.csv                  # Sample test data
└── README.md                 # This file

```

## 📄 Sample CSV Data (`users.csv`)
```csv
name,email,newEmail
"John Doe","john@example.com","john.new@example.com"
"Jane Smith","jane@example.com","jane.new@example.com"
"Bob Johnson","bob@example.com","bob.updated@example.com"
```

## 🎯 Usage Examples

### Dynamic JSON Payloads
**POST Create User:**
```json
{
  "name": "${name}",
  "email": "${email}"
}
```

**PATCH Update Email:**
```json
{
  "email": "${newEmail}"
}
```

### Complete Workflow
1. **POST** `/users` → Creates user (expects **201**)
2. **GET** `/users/${userId}` → Verifies creation (**200**)
3. **PATCH** `/users/${userId}` → Updates email (**200**)
4. **DELETE** `/users/${userId}` → Deletes user (**200**)
5. **GET** `/users/${userId}` → Confirms deletion (**404**)

## 📊 Expected Results

| Request     | Expected Status | Assertion |
|-------------|-----------------|-----------|
| POST        | 201 Created     | ✅ Pass   |
| GET (Read)  | 200 OK          | ✅ Pass   |
| PATCH       | 200 OK          | ✅ Pass   |
| DELETE      | 200 OK          | ✅ Pass   |
| GET (Verify)| 404 Not Found   | ✅ Pass   |

## 🔧 Troubleshooting

| Issue                          | Solution                                      |
|--------------------------------|-----------------------------------------------|
| "CSV Data Set not found"       | Put `users.csv` in same folder as `.jmx`      |
| "Connection timeout"           | Check internet connectivity                   |
| "JMeter not found"             | Add JMeter `bin` folder to PATH               |
| Assertions failing             | Check View Results Tree for response details  |


</div>
