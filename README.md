# 🧾 Oracle Integration Cloud – Invoke BIP Report Using SOAP Web Services

## 📌 Project Overview

This project demonstrates how to **invoke an Oracle BI Publisher (BIP) report** using **SOAP web services** within **Oracle Integration Cloud (OIC)**. 
The goal is to automate the extraction of report data (such as invoices, payments, suppliers, etc.) from Oracle ERP Cloud and consume the result in downstream systems.

---

## 🎯 Use Case

- A business needs to retrieve a BIP report (e.g., Payables Invoice Register).
- The integration calls the **ERP SOAP endpoint** to invoke the BIP report.
- The report is generated and returned as **Base64-encoded content**.
- The content can be saved to a file, sent to email, or delivered to an external system.

---

## 🔧 Technologies Used

- Oracle Integration Cloud (OIC)
- SOAP Adapter
- ERP Cloud BI Publisher (BIP)
- Base64 decoding
- File / Email / REST Adapter (optional)

---

## 🪜 Step-by-Step Implementation

### 1. **Create ERP SOAP Connection**

- Adapter: SOAP
- WSDL URL:
- - **Security Policy**: Username Token
- **Authentication**: Provide ERP Cloud credentials with necessary permissions.

### 2. **Design Integration Flow**

- **Type**: Scheduled Orchestration
- **Steps**:
1. **Invoke SOAP Service**: Use the `runReport` operation.
2. **Configure Request Parameters**:
   - `reportAbsolutePath`: Absolute path to the BIP report (e.g., `/Custom/Reports/AP/PayablesInvoiceReport.xdo`).
   - `attributeFormat`: Desired output format (`pdf`, `csv`, etc.).
   - `attributeName & Item`.
   - `sizeOfDataChunkDownload`: Set to `-1` to retrieve the entire report in one response.
3. **Decode Base64 Response**: Utilize the `decodeBase64()` function to convert the `reportBytes` to binary data.
4. **Deliver Report**: Optionally, write the decoded report to an FTP server or send it via email.

### 3. **Activate and Test Integration**

- **Activation**: Deploy and activate the integration in OIC.
- **Testing**: Monitor the integration run, verify the report retrieval, and ensure successful delivery to the intended destination.

---

## ✅ Benefits

- **Automation**: Eliminates manual retrieval of BIP reports.
- **Efficiency**: Streamlines report distribution processes.
- **Scalability**: Easily extendable to handle multiple reports and destinations.
- **Maintainability**: Centralized integration logic within OIC.


