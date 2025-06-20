Here’s a simple and clear **Python script to parse Apache access logs** and **count the number of occurrences of each HTTP status code** (e.g., 200, 404, 500, etc.).

---

## ✅ **Python Script: Count HTTP Status Codes in Apache Logs**

```python
import re
from collections import Counter

# Path to your Apache log file
log_file_path = 'access.log'

# Regular expression to match status codes from common Apache log format
log_pattern = re.compile(r'"\s(\d{3})\s')

# Counter to store the occurrences
status_codes = Counter()

# Read and parse the log file
with open(log_file_path, 'r') as file:
    for line in file:
        match = log_pattern.search(line)
        if match:
            status_code = match.group(1)
            status_codes[status_code] += 1

# Print results
print("HTTP Status Code Counts:")
for code, count in status_codes.items():
    print(f"Status Code {code}: {count} times")
```

---

## 🔍 **What this script does:**

1. Reads Apache log file line by line.
2. Extracts the HTTP response status code using **regex**.
3. Counts the occurrence of each code.
4. Prints the summary.

---

## ✅ **Example Apache Log Line Supported:**

```
127.0.0.1 - - [20/Jun/2025:13:55:36 +0000] "GET /index.html HTTP/1.1" 200 1043
```

The **status code 200** will be extracted from such a line.

---

## ✅ **Output Example:**

```
HTTP Status Code Counts:
Status Code 200: 150 times
Status Code 404: 3 times
Status Code 500: 1 times
```

---

## ⚠️ Notes:

* This works for **Common and Combined Log Formats**.
* If your logs have a different structure — tell me — I’ll adjust the regex.
* For large files, this script handles them efficiently line by line.

---

Do you want this **as part of a Jenkins shared library example** (as per your previous questions)?
Or would you like it to **output JSON / CSV format**?
Let me know!
