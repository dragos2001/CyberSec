# 🛡️ PCAP-Based Intrusion Detection Using a Local LLM 🤖

## 📌 Project Overview

This project analyzes network traffic captured in **PCAP files** to identify potential cyber attacks. It focuses on detecting three specific attack types:

- 🌊 **SYN Flood**
- 🔍 **Port Scanning**
- 🗄️ **DNS Exfiltration**

The system combines **traditional packet analysis and traffic aggregation** with a **locally hosted Large Language Model (LLM)**. The LLM is used to classify and explain suspicious network behavior based on summarized traffic patterns.

All processing is performed **locally**, without reliance on cloud-based APIs, ensuring 🔐 **data privacy**.

---

## 🏗️ System Architecture

![System Architecture](system_architecture.png)
<p style="font-size:16px; text-align:center;">
Figure 1: System architecture for PCAP-based intrusion detection using traffic aggregation and a local LLM for classification and explanation.
</p>

---

## ✨ Key Features

- 📦 Parses PCAP files using packet inspection  
- 📊 Aggregates traffic by IP addresses, ports, DNS queries, and time  
- 🚨 Detects SYN floods, port scans, and DNS exfiltration  
- 🤖 Uses a **local LLM** for attack classification and reasoning  
- 📝 Produces human-readable explanations for detected attacks  

---

## 🧠 Attack Detection Approach

### 🌊 SYN Flood Detection
- Aggregates TCP traffic by source and destination IP  
- Tracks the number of TCP SYN and ACK packets  
- Summarizes traffic duration and packet imbalance  
- LLM determines whether the behavior matches a SYN flood  

### 🔍 Port Scan Detection
- Aggregates TCP traffic by source IP  
- Tracks the number of unique destination ports contacted  
- Summarizes scanning behavior over time  
- LLM determines whether the behavior matches a port scan  

### 🗄️ DNS Exfiltration Detection
- Aggregates DNS queries by source IP  
- Tracks query frequency and query length  
- Highlights unusually long or frequent DNS queries  
- LLM determines whether the behavior matches DNS exfiltration  

---

## 🤖 Role of the Local LLM

The LLM is used as a **semantic classification and explanation layer**, not as a low-level packet classifier.

Specifically, the LLM:
- Receives summarized traffic descriptions  
- Classifies traffic as one of:
  - 🌊 SYN Flood  
  - 🔍 Port Scan  
  - 🗄️ DNS Exfiltration  
  - ✅ Benign  
- 🧾 Generates natural-language explanations describing its reasoning  

This design improves interpretability while keeping detection efficient and modular.

---

## 🗂️ Dataset Usage

A labeled network traffic dataset was used to:

- 🔎 Study common patterns associated with SYN floods, port scans, and DNS exfiltration  
- 🧪 Select relevant packet and flow-level features  
- 🧠 Validate aggregation logic and detection behavior  
- ✍️ Inform LLM prompt design  

⚠️ The dataset was **not used to fine-tune the LLM**. Detection logic is based on aggregation, while the LLM provides reasoning and classification.

---



