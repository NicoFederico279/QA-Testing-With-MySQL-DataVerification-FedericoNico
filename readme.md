# Quality Assurance Testing (QAT) Toolkit: Portfolio Repository

> **Source File Reference:** `textcase.txt`  
> **Project Title:** AI-Generated Web Application Verification

---

## 1. Repository Structure & Artifacts

This repository serves as a Quality Assurance Testing (QAT) toolkit containing test artifacts, execution documentation, and technical reference files for an AI-generated web application.

```text
├── readme.md                       # [Part A] Test case documentation and execution matrix
├── webapp-generation-prompt.txt    # [Part B] AI generation prompt used to create the web app
└── test-webapp.php                 # [Part C] Single-file PHP web application source code
```

---

## 2. Test Case Documentation

### 2.1 Metadata & Parameters

| Parameter | Information |
| :--- | :--- |
| **Test Case ID** | `TC-DataEntry-001` |
| **Test Case Title** | Data Entry - Valid |
| **Test Description** | Functional testing of Data Entry page with backend validation using MySQL queries. |
| **Preconditions** | Kara David Birthday Wishnote App installed locally; MySQL database initialized; data entry page accessed via modern web browser (Chrome/Firefox). |
| **Test Data** | Five (5) valid entries containing First Name, Last Name, Government Position, and Location within character constraints. |
| **Execution Status** | **`FAILED`** |

---

### 2.2 Test Execution Matrix

| Step | Action | Expected Result | Actual Result |
| :---: | :--- | :--- | :--- |
| **a** | Verify that the form contains labels in proper order and the text boxes are writable. | The form contains labels in this order: "First Name", "Last Name", "Government Position", and "Location"; all text boxes are writable. | The form contains labels in this order: "First Name", "Last Name", "Government Position", and "Location"; all text boxes are writable. |
| **b** | Verify the "Send Wish Note" button. | The "Send Wish Note" button changes color on hover and is not disabled. | The "Send Wish Note" button changes color on hover and is not disabled. |
| **c** | Enter test data on their respective fields. | The respective fields accept data entries of valid test data. | The respective fields accept data entries of valid test data. |
| **d** | Click the "Send Wish Note" button. | A modal dialog appears displaying the submitted information. | A modal dialog appeared on screen presenting the entered details. |
| **e** | Verify if the modal contains the same entry as your test data. | The modal displays exact matching data for First Name, Last Name, Government Position, and Location. | The modal displayed the exact matching entries for all four fields. |
| **f** | Click the Cancel button. | The modal closes without submitting the form data. | The modal dismissed properly without sending data. |
| **g** | Click again on "Send Wish Note" button, then click "Confirm and Send" inside the modal. | Form submits data to the backend script. | Form submitted successfully via POST request. |
| **h** | Verify if a successful entry message shows on the Data Entry page. | "Success! The wish note has been sent." message is displayed. | The message "Success! The wish note has been sent." was displayed on top of the page. |
| **i** | Verify the test data in the MySQL database. | Database table `main_corrupt_politicians` records all four fields correctly including `Location`. | Database query output shows `FirstName`, `LastName`, and `GovPosition` inserted successfully, but `Location` remains `NULL` because the backend PHP script omits the column from the `INSERT` query:<br><br>```text\n+----+-----------+----------+-----------------+----------+\n| id | FirstName | LastName | GovPosition     | Location |\n+----+-----------+----------+-----------------+----------+\n|  1 | Juan      | Dela Cruz| Governor        | NULL     |\n+----+-----------+----------+-----------------+----------+\n``` |