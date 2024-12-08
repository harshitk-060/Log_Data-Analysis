# **Log Analysis Tool**

This Python-based tool analyzes server log files to provide meaningful insights, such as requests per IP, the most accessed endpoint, and suspicious activities like brute force login attempts. It efficiently processes log files, displays the results in a terminal-friendly format, and saves the analysis to a CSV file for further use.

---

## **Features**

1. **Requests per IP**:
   - Extracts all IP addresses from the log file.
   - Counts the number of requests made by each IP address.
   - Displays results sorted in descending order of request counts.

2. **Most Accessed Endpoint**:
   - Identifies the most frequently accessed URL or resource path.
   - Displays the endpoint name and the number of times it was accessed.

3. **Suspicious Activity Detection**:
   - Detects IP addresses involved in failed login attempts (e.g., HTTP status code `401` or "Invalid credentials").
   - Flags IPs with failed login attempts exceeding a configurable threshold (default: 10).
   - Displays these flagged IPs along with their failed login counts.

4. **Output**:
   - Displays the analysis results in the terminal in an organized format.
   - Saves the results to a CSV file (`log_analysis_results.csv`) with three sections:
     - Requests per IP
     - Most Accessed Endpoint
     - Suspicious Activity

---

## **Project Structure**

```plaintext
.
├── log_analysis.py         # Main Python script
├── sample.log              # Sample log file for testing
├── log_analysis_results.csv # Output CSV file (generated after running the script)
├── README.md               # Project documentation
```

---

## **Prerequisites**

- Python 3.6 or above
- Log file to analyze (in standard format, such as Apache or Nginx logs)

### **Required Python Libraries**
The script uses only Python's standard library, so no additional installations are required.

---

## **How to Use**

### **1. Clone the Repository**
```bash
git clone <repository_url>
cd <repository_directory>
```

### **2. Place the Log File**
Place the log file (e.g., `sample.log`) in the same directory as the script.

### **3. Run the Script**
```bash
python log_analysis.py
```

### **4. View Results**
- The results will be displayed in the terminal.
- A CSV file (`log_analysis_results.csv`) will be created in the same directory containing:
  - **Requests per IP**: IP address and request count.
  - **Most Accessed Endpoint**: Endpoint name and its access count.
  - **Suspicious Activity**: IP address and failed login attempt count.

---

## **CSV Output Example**

After running the script, the `log_analysis_results.csv` file will look like this:

```plaintext
Requests per IP
IP Address,Request Count
192.168.1.1,234
203.0.113.5,187
10.0.0.2,92

Most Accessed Endpoint
Endpoint,Access Count
/home,403

Suspicious Activity
IP Address,Failed Login Count
192.168.1.100,56
203.0.113.34,12
```

---

## **Terminal Output Example**

### **Requests per IP**:
```
Requests per IP:
IP Address           Request Count
192.168.1.1          234
203.0.113.5          187
10.0.0.2             92
```

### **Most Frequently Accessed Endpoint**:
```
Most Frequently Accessed Endpoint:
Endpoint: /home (Accessed 403 times)
```

### **Suspicious Activity Detected**:
```
Suspicious Activity Detected:
IP Address           Failed Login Count
192.168.1.100        56
203.0.113.34         12
```

---

## **Configuration**

### **Threshold for Suspicious Activity**
To change the default threshold for failed login attempts (default is `10`), modify the `threshold` value in the script:

```python
threshold = 10  # Change this value as needed
```

---

## **Code Overview**

### **Main Functions**
1. **`parse_log_file(file_path)`**:
   - Reads and parses the log file line-by-line.
   - Extracts IP addresses, endpoints, and failed login attempts.

2. **`find_most_accessed_endpoint(endpoint_requests)`**:
   - Identifies the endpoint with the highest number of requests.

3. **`filter_suspicious_ips(failed_logins, threshold)`**:
   - Filters IPs with failed login attempts exceeding the threshold.

4. **`save_results_to_csv(ip_requests, most_accessed_endpoint, suspicious_ips, output_file)`**:
   - Writes analysis results to a CSV file.

5. **`display_results(ip_requests, most_accessed_endpoint, suspicious_ips)`**:
   - Displays the results in the terminal.

### **Workflow**
1. The script reads the log file and extracts relevant information.
2. Results are computed for:
   - Requests per IP
   - Most accessed endpoint
   - Suspicious activity
3. Results are displayed in the terminal and saved to a CSV file.

---

## **Testing**

### **Run with a Sample Log File**
- Use the included `sample.log` file for testing.
- Ensure the script outputs correct results for requests per IP, most accessed endpoint, and suspicious activity.

---

## **Performance**

- The script processes logs line-by-line, ensuring low memory usage and scalability for large log files.
- Utilizes Python's `collections.Counter` for efficient counting operations.

---

## **Customization**

- **Log Format**: The script assumes a standard log format (e.g., Apache or Nginx logs). Adjust the parsing logic in `parse_log_file` if your log file has a different structure.
- **Output File**: Change the default CSV output file name by modifying the `output_file` parameter in `save_results_to_csv`.

---

## **Future Enhancements**

- Add support for more log formats.
- Implement filtering options (e.g., by date or specific endpoints).
- Provide a graphical interface for viewing analysis results.

---

## **Contributors**

- **[Your Name]** – Developer
- Contributions are welcome! Feel free to open issues or submit pull requests.

---

## **License**

This project is licensed under the MIT License. See the `LICENSE` file for details.
