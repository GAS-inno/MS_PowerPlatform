Here’s a well-structured **README.md** file for your GitHub project based on the provided code and context. This README will help users understand the purpose of your project, how to use it, and what it does.

---

# Singtel Invoice Processing Automation

## **Overview**
This project automates the extraction and processing of invoice data from Singtel PDF files. The extracted data is written to an Excel file for further analysis and reporting. The automation script is designed to:
- Extract specific fields (e.g., Bill Date, Account Name, GST Charges) from PDF invoices using regular expressions.
- Map account names to cost centers based on predefined mappings.
- Write the processed data into an Excel file.

## **Features**
- **PDF Text Extraction**: Extracts text from PDF invoices.
- **Regex-Based Data Parsing**: Uses regular expressions to identify and extract key invoice details.
- **Cost Center Mapping**: Matches account names to their respective cost centers.
- **Excel Integration**: Writes the processed data into an Excel file for easy access and analysis.

## **Project Structure**
```
Singtel_Invoices/
├── Input/                # Folder containing input PDF invoices
├── Output/               # Folder where the processed Excel file is saved
├── Singtel_invoice_ExtractedPDFText.xlsx  # Output Excel file
├── main_script           # Main automation script
└── README.md             # Project documentation
```

## **Requirements**
- **Software**: 
  - Microsoft Excel (for Excel integration)
  - PDF reader (for PDF text extraction)
- **Dependencies**: Ensure the following libraries/tools are installed:
  - Python (if applicable)
  - Any required automation tools or libraries (e.g., PDF text extraction libraries, Excel libraries)

## **Setup**
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/Singtel_Invoices.git
   ```
2. Navigate to the project directory:
   ```bash
   cd Singtel_Invoices
   ```
3. Place the input PDF invoices in the `Input/` folder.

## **Usage**
1. **Run the PowerAutomate Desktop Flow**: Execute the automation script to process the invoices.
2. **Output**: The processed data will be saved in the `Output/Singtel_invoice_ExtractedPDFText.xlsx` file.

## **How It Works**
1. **PDF Extraction**: The script reads all PDF files in the `Input/` folder.
2. **Regex Matching**: It uses predefined regular expressions to extract specific fields from the PDF text:
   - **Bill Date**: Extracted using the pattern `(?<=Bill Date\\r\\n).+\\d{4}`
   - **Account Name**: Extracted using the pattern `(?<=Account No\\. Total Due \\(SGD\\)\\s)\\d+`
   - **GST Charges**: Extracted using the pattern `(?<=Current Taxable Charges of SGD)[\\d,]+\\.\\d{2}`
   - **Zero Rated Charges**: Extracted using the pattern `(?<=Zero Rated Charges of SGD)[\\d,]+\\.\\d{2}`
3. **Cost Center Mapping**: Matches account names to cost centers using a predefined mapping table.
4. **Excel Writing**: Writes the extracted and processed data into the Excel file.

## **Customization**
- **Regex Patterns**: Update the regular expressions in the script to match your specific invoice format.
- **Cost Center Mapping**: Modify the `CostCentreTable` to include additional account names and their corresponding cost centers.

## **Example Output**
Here’s an example of the data written to the Excel file:
| Bill Date | Account Name | GST Charges | Zero Rated Charges | Cost Centre       |
|-----------|--------------|-------------|---------------------|-------------------|
| 01/01/2025 | 1234556     | 100.00      | 0.00                | P12344557        |

## **Contributing**
Contributions are welcome! If you have suggestions or improvements, feel free to open an issue or submit a pull request.

---
# Desktop Flow Screenshot Detail
![image](https://github.com/user-attachments/assets/5a41b205-81e0-4eba-80aa-17f8f48ee91c)
![image](https://github.com/user-attachments/assets/c3b7365a-21ef-4722-acd3-3e5eb0903151)
![image](https://github.com/user-attachments/assets/653ea33e-5534-465a-9c2e-6f590d9a3281)



This README provides a clear and concise explanation of your project, making it easy for others to understand and use. Let me know if you'd like to add or modify anything!
