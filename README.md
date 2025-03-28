# 🚀 AI-powered Log Analysis with Anomaly Detection

## 📌 Overview

This project is an AI-driven **log analysis system** designed to detect **anomalies, error spikes, and suspicious activities** in system logs. It uses **Python, Pandas, and Regex** to process logs, count error occurrences, and detect patterns that indicate security threats or system health issues.

## 🔍 Features

- ✅ **Automated Log Parsing** – Extracts structured data from unstructured logs.
- 🚨 **Anomaly Detection** – Detects excessive errors in short time windows.
- 🛡️ **Security Insights** – Identifies unauthorized access attempts, brute force attacks, and rate limit violations.
- ⚡ **Performance Monitoring** – Flags high CPU usage, slow queries, and service failures.
- 📊 **Summarization & Reporting** – Provides insights into the most frequent log levels and issues.

## 🛠️ Tech Stack

- **Python** 🐍 (Pandas, Collections, Regex)
- **Jupyter Notebook / Python Scripts**
- **AIOps** concepts for log monitoring

## 📂 Sample Log Data

Here’s a snippet of the type of logs processed:

```
2025-03-27 10:00:36 ERROR API request received: POST /order
2025-03-27 10:01:44 ERROR CPU usage at 95%
2025-03-27 10:02:38 ERROR Database connection failed
2025-03-27 10:06:45 ERROR Unauthorized access attempt to admin panel
2025-03-27 10:03:06 CRITICAL Database connection failed
```

## 📊 Insights & Observations

🔹 **Error Spike Detection:**

- Multiple errors occurred within short time spans (e.g., API failures, DB issues, high CPU usage), indicating possible performance bottlenecks.
- Example: **3+ ERROR logs detected within 30 seconds** at multiple timestamps.

🔹 **Security Alerts:**

- **Brute Force Protection Activated** multiple times, indicating repeated unauthorized login attempts.
- **Unauthorized Admin Panel Access Attempts** suggest a potential attack.

🔹 **System Health Issues:**

- **Database Disk Space Low** warnings may indicate storage problems.
- **Service Restarts & Dependency Failures** hint at instability in dependent services.

## ⚙️ How It Works

```python
import pandas as pd
from collections import Counter
import re

# Load logs and parse timestamp, level, and message
log_entries = []
with open("system_logs.txt", "r") as file:
    for line in file:
        match = re.match(r"(\d{4}-\d{2}-\d{2} \d{2}:\d{2}:\d{2}) (\w+) (.+)", line.strip())
        if match:
            log_entries.append(match.groups())

df = pd.DataFrame(log_entries, columns=["timestamp", "level", "message"])
df["timestamp"] = pd.to_datetime(df["timestamp"])

# Detect error spikes
error_counts = Counter(df[df["level"] == "ERROR"]["timestamp"].dt.floor("30S"))
threshold = 3
for time, count in error_counts.items():
    if count > threshold:
        print(f"🚨 Anomaly detected! {count} ERROR logs in 30 seconds at {time}")
```

## 📌 Future Enhancements

- ✅ Integrate **Machine Learning for log anomaly prediction**.
- ✅ Use **Grafana / Kibana** for real-time visualization.
- ✅ Implement **AI-driven automated responses** (e.g., block IPs, restart services).

## ⭐ Contribute

Want to improve this AI-driven log monitoring tool? Feel free to fork and submit a pull request! 🚀

📌 **GitHub Repo:** [Coming Soon]
📌 **LinkedIn Post:** Check out the insights below! ⬇️



