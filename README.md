# Advanced Gitleaks JSON Visualizer

A sophisticated client-side HTML tool for parsing, visualizing, filtering, and analyzing Gitleaks JSON reports. This visualizer provides an intuitive interface to make reviewing security leaks more efficient and user-friendly.

> [!NOTE]
> MADE BY : Gemini 2.5 pro 😝

## 🚀 Overview

Gitleaks is an excellent tool for finding secrets in git repositories. However, its JSON output can sometimes be overwhelming to parse manually. The **Advanced Gitleaks JSON Visualizer** transforms this raw JSON data into an interactive, human-readable format directly in your browser. No server-side setup is required; simply open the HTML file and load your report.

## ✨ Features

*   **📁 Easy File Upload**:
    *   Drag & drop your Gitleaks JSON report.
    *   Standard file selection dialog.
    *   Instant parsing and display.
*   **💅 Rich Visualization**:
    *   Leaks displayed in clean, organized cards.
    *   Color-coded rule IDs for quick identification of leak types.
    *   Key information (RuleID, File, Description, Match snippet) visible at a glance.
*   **🔍 Advanced Filtering**:
    *   Filter by **RuleID** (contains match).
    *   Filter by **File Path** (contains match).
    *   Filter by **Author** (contains match).
    *   Filter by **Commit Hash** (contains match).
    *   Filter by **Date Range** (start and end dates).
*   **🔧 View & Display Controls**:
    *   **Sort Leaks**: By Date (Newest/Oldest), RuleID, File Path, or Entropy (High/Low).
    *   **Customize Card Content**: Toggle visibility of Author, Commit Hash, and Entropy on leak cards.
    *   **Summary Count**: See "Displaying X of Y total leaks" to understand filter impact.
*   **📄 Detailed Leak Modal**:
    *   Click on any leak card to open a modal with comprehensive details.
    *   Includes all fields from the Gitleaks JSON entry (e.g., Secret, Match, Commit, Author, Date, Entropy, Fingerprint).
    *   Provides rule-specific remediation **recommendations**.
*   **📜 Collapsible Sections**:
    *   Dedicated, toggleable sections for File Upload, Filters & View Options, and CI/CD Integration Info to keep the interface clean.
*   **🔗 CI/CD Integration Guidance**:
    *   A built-in section explains how this visualizer can be used with CI/CD pipeline artifacts.
*   **📱 Responsive Design**:
    *   Adapts to various screen sizes for usability on desktops and tablets.
*   **🛡️ Client-Side Security**:
    *   All processing is done in your browser. Your Gitleaks report is not uploaded to any server.
    *   Content is sanitized to prevent XSS from JSON data.

## 🛠️ How to Use

1.  **Save the Tool**:
    *   You will have an HTML file (e.g., `gitleaks_visualizer.html`). Save this file to your local machine.
2.  **Open in Browser**:
    *   Open the saved HTML file in your preferred web browser (e.g., Chrome, Firefox, Edge, Safari).
3.  **Upload Gitleaks Report**:
    *   Run Gitleaks on your repository and ensure the output is in JSON format.
        ```bash
        gitleaks detect --report-format json --report-path gitleaks-report.json -v
        ```
    *   In the visualizer, drag and drop your `gitleaks-report.json` file onto the designated area, or click to select it using the file dialog.
4.  **Analyze Leaks**:
    *   The visualizer will automatically parse the JSON and display the detected leaks.
    *   Use the filter and sort options in the "Filters & View Options" section to refine the view.
    *   Click on any leak card to see full details in a modal window.

## 📝 Example Gitleaks JSON Structure

The visualizer expects a JSON array with objects similar to this structure for each leak:

```json
[
  {
    "Description": "Detected a JWT token...",
    "StartLine": 1310,
    "EndLine": 1310,
    "StartColumn": 1,
    "EndColumn": 100,
    "Match": "Authorization: Bearer eyJhbGciOiJIUzI1NiIsIrR5cXI6IkpXCCJ6...",
    "Secret": "eyJhbGciOiJIUzI1NiIsIrR5cXI6IkpXCCJ6...",
    "File": "example-web/WebContent/WEB-INF/Main.properties",
    "SymlinkFile": "",
    "Commit": "xxxxxxxxeb8fc0a4ee49bdd75ddee8xxxxxxxxxx",
    "Entropy": 4.123,
    "Author": "JohnDoe",
    "Email": "john.doe@example.com",
    "Date": "2020-05-02T05:28:45Z",
    "Message": "Merge changes from release/beta...",
    "Tags": [],
    "RuleID": "jwt",
    "Fingerprint": "xxxxxxxxeb8fc0a4ee49bdd75ddee8xxxxxxxxxx:..."
  }
  // ... more leak objects
]
```

## 📝 Example UI output

![Gitleaks Visualizer Demo](image.png)
![Gitleaks Visualizer Demo](image2.png)