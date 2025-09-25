# Ex.No.6 Development of Python Code Compatible with Multiple AI Tools

# Date:25/09/2025
# Register no.212223220069
# Aim: Write and implement Python code that integrates with multiple AI tools to automate the task of interacting with APIs, comparing outputs, and generating actionable insights with Multiple AI Tools

# Procedure:
Understanding the Persona Pattern in AI integration
Developing Python code to read both .csv and .json into a list of dictionaries
Explaining the code with diagrams/images

# Explanation:
Experiment the persona pattern as a programmer for any specific applications related with your interesting area. 
Generate the outoput using more than one AI tool and based on the code generation analyse and discussing that. 

1. The Persona Pattern in AI Integration
The Persona Pattern in software/AI systems means designing a single general-purpose interface (a "persona") that interacts with multiple AI tools or APIs.

Instead of writing tool-specific code everywhere, you define a single function that handles different file formats (CSV, JSON, etc.) or AI APIs.
This makes your system scalable, reusable, and modular.
In this experiment, your persona is a unified function that can read both .csv and .json files into the same format (list of dictionaries).

2. Python Code Implementation
Here’s the Python code:
```
import csv
import json
import os

def read_file_as_dicts(file_path):
    """
    Reads a .csv or .json file and returns a list of dictionaries.
    Works as a 'persona pattern' since the same function adapts to different inputs.
    """
    # Check if file exists
    if not os.path.exists(file_path):
        raise FileNotFoundError(f"File '{file_path}' not found.")

    # Extract extension
    extension = os.path.splitext(file_path)[1].lower()

    # For CSV files
    if extension == ".csv":
        with open(file_path, mode="r", encoding="utf-8") as f:
            reader = csv.DictReader(f)
            data = [row for row in reader]  # each row is already a dictionary
        return data

    # For JSON files
    elif extension == ".json":
        with open(file_path, mode="r", encoding="utf-8") as f:
            data = json.load(f)
            # Ensure it returns a list of dictionaries
            if isinstance(data, dict):
                data = [data]
        return data

    else:
        raise ValueError("Unsupported file format. Use .csv or .json")


# ---------------- Example Usage ----------------
if __name__ == "__main__":
    csv_data = read_file_as_dicts("data.csv")
    json_data = read_file_as_dicts("data.json")

    print("CSV Data:", csv_data)
    print("JSON Data:", json_data)
```
3. Explanation with Diagrams
Input Files
CSV File (data.csv):
```
name,age,city
Hema,21,Chennai
Arun,23,Bangalore
```
JSON File (data.json):
```
[
  {"name": "Hema", "age": 21, "city": "Chennai"},
  {"name": "Arun", "age": 23, "city": "Bangalore"}
]
```
Function Flow
Here’s a flow diagram of how the function works:

Image 1: Function Workflow
```

 ┌───────────────┐
 │ Input File     │
 │ (.csv / .json) │
 └───────┬───────┘
         │
         ▼
 ┌─────────────────┐
 │ Identify Format  │
 └───────┬─────────┘
     CSV │ JSON
         ▼
 ┌───────────────┐
 │ Parse Content │
 │   DictReader  │
 │   json.load   │
 └───────┬───────┘
         ▼
 ┌─────────────────────┐
 │ List of Dictionaries │
 └─────────────────────┘
```
Image 2: Unified Output

No matter the input format, output is always:
```

[
  {"name": "Hema", "age": "21", "city": "Chennai"},
  {"name": "Arun", "age": "23", "city": "Bangalore"}
]
```
# Conclusion:
Why This Fits the Persona Pattern

A single function behaves like a persona, adapting to both CSV and JSON.
The output is always standardized, making it easy to integrate with AI tools (e.g., OpenAI API, Gemini, Claude, etc.).
You can extend the same function later to support XML, Excel, or APIs.


# Result: The corresponding Prompt is executed successfully.
