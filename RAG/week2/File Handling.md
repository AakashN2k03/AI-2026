
# Python File Handling

## 1. What is File Handling?

File handling in Python allows us to create, read, write, and update files.

It is useful for:
- Storing data permanently.
- Reading configuration files.
- Working with JSON data.
- Loading documents for AI and RAG applications.

---

## 2. Opening a File

We use the `open()` function to open a file.

```python
file = open("notes.txt", "r")
```

Syntax:

```python
open("filename", "mode")
```

- `filename`: Name of the file.
- `mode`: Specifies what operation we want to perform.

---

## 3. File Modes

| Mode | Description |
|---|---|
| `"r"` | Read an existing file |
| `"w"` | Write; overwrites existing content or creates a file |
| `"a"` | Append content to the end of a file or create it |
| `"x"` | Create a new file; raises an error if it already exists |
| `"rb"` | Read a file in binary mode |
| `"wb"` | Write a file in binary mode |

Example:

```python
with open("notes.txt", "w") as file:
    file.write("Learning Python")
```

This creates `notes.txt` if it doesn't exist. If it already exists, its previous content is overwritten.

---

## 4. The `with` Statement

The `with` statement automatically closes the file after the block finishes.

```python
with open("notes.txt", "r") as file:
    content = file.read()
    print(content)
```

**Why use `with`?**

- Automatically closes the file.
- Helps manage resources safely.
- Avoids manually calling `file.close()`.

---

## 5. Reading a File

### `read()`

Reads the entire file content as a string.

```python
with open("notes.txt", "r") as file:
    content = file.read()
    print(content)
```

### `readline()`

Reads one line at a time.

```python
with open("notes.txt", "r") as file:
    print(file.readline())
```

### `readlines()`

Reads all lines and returns a list of strings.

```python
with open("notes.txt", "r") as file:
    lines = file.readlines()
    print(lines)
```

If the file contains:

```text
Python
FastAPI
RAG
```

The output of `readlines()` is:

```python
['Python\n', 'FastAPI\n', 'RAG']
```

The `\n` represents a newline character.

---

## 6. Writing to a File

The `"w"` mode creates a file or overwrites its existing content.

```python
with open("notes.txt", "w") as file:
    file.write("Python\n")
    file.write("FastAPI\n")
    file.write("RAG\n")
```

File content:

```text
Python
FastAPI
RAG
```

**Important:** Opening an existing file in `"w"` mode clears its previous content.

---

## 7. Appending to a File

The `"a"` mode adds content to the end of a file without removing existing content.

```python
with open("notes.txt", "a") as file:
    file.write("Machine Learning\n")
```

If the previous content was:

```text
Python
FastAPI
RAG
```

The new content becomes:

```text
Python
FastAPI
RAG
Machine Learning
```

Note: `write()` does not automatically add a newline. Use `\n` when required.

---

## 8. Handling File Errors

If we try to read a file that doesn't exist, Python raises `FileNotFoundError`.

We can handle it using `try` and `except`.

```python
try:
    with open("missing.txt", "r") as file:
        content = file.read()
        print(content)

except FileNotFoundError:
    print("File not found!")
```

Output:

```text
File not found!
```

This prevents the program from terminating unexpectedly because of this error.

---

## 9. JSON File Handling

JSON stands for **JavaScript Object Notation**. It is a common format for storing and exchanging structured data.

Python provides the built-in `json` module.

```python
import json
```

### `json.dump()` — Write Python Data to a JSON File

```python
import json

user = {
    "name": "Arun",
    "age": 25,
    "skills": ["Python", "FastAPI"]
}

with open("user.json", "w") as file:
    json.dump(user, file, indent=4)
```

This creates `user.json` and writes the dictionary into it.

Resulting file:

```json
{
    "name": "Arun",
    "age": 25,
    "skills": [
        "Python",
        "FastAPI"
    ]
}
```

**Explanation:**

- `open("user.json", "w")`: Opens the file in write mode.
- `as file`: Stores the file object in the variable `file`.
- `json.dump(user, file, indent=4)`: Writes the dictionary to the file as formatted JSON.
- `indent=4`: Makes the JSON easier to read by indenting nested data with four spaces.

### `json.load()` — Read Data from a JSON File

```python
import json

with open("user.json", "r") as file:
    data = json.load(file)

print(data["name"])
print(data["age"])
```

Output:

```text
Arun
25
```

`json.load()` reads the JSON file and converts its content into equivalent Python data types, such as dictionaries and lists.

---

## 10. `dump()` vs `dumps()` vs `load()` vs `loads()`

| Function | Purpose |
|---|---|
| `json.dump()` | Writes Python data into a JSON file |
| `json.dumps()` | Converts Python data into a JSON string |
| `json.load()` | Reads JSON data from a file |
| `json.loads()` | Converts a JSON string into Python data |

Example of `dumps()`:

```python
import json

user = {"name": "Arun", "age": 25}

json_string = json.dumps(user)

print(json_string)
print(type(json_string))
```

Output:

```text
{"name": "Arun", "age": 25}
<class 'str'>
```

Unlike `dump()`, `dumps()` returns a string rather than writing directly to a file.

---

## 11. Quick Revision

- `open()` opens a file.
- `"r"` reads a file.
- `"w"` creates or overwrites a file.
- `"a"` appends content.
- `"x"` creates a new file only if it doesn't already exist.
- `with` automatically closes the file.
- `read()` reads the entire file.
- `readline()` reads one line.
- `readlines()` returns a list of lines.
- `write()` writes a string to a file.
- `json.dump()` writes Python data to a JSON file.
- `json.load()` reads a JSON file into Python data.
- `json.dumps()` converts Python data into a JSON string.
- `json.loads()` converts a JSON string into Python data.

---
