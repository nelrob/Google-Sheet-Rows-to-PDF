# Google-Sheet-Rows-to-PDF
Google Apps Script to generate PDF/s from a single or multiple Google Sheet row/s. 

Template files are available in the repo to play with.

This script works by:
- Getting a user's input on which row/s they want to generate a PDF from,
- parsing the row's by matching the Sheets data with the `{{placeholder}}` set in the template document,
- ponverting the row values into the template document,
- generating a PDF from the template document.

## Features 
- Skips a row if a PDF has already been generated
- Sheets UI to:
    - prompt input from the user to configure single or multiple PDF generation
    - prompt input from the user to enter number of rows to be generated
    - show progress of PDF generation
    - show PDF link/s
    - show if row/s have been skipped
    - show errors 

## Prerequisites
1. Google Sheets data with at least the following column headers:
  - ID (to show the ID in the file name)
  - Name (to show the Name in the file name)
  - Status (to insert the generated PDF's link)
2. Google Drive folder for where the PDFs will be contained - user must have edit permissions
3. ID of above Google Drive folder (e.g. https://docs.google.;com/document/d/XXXXXXXX_XXX/edit?usp=drive_link)
4. Google Doc template that the PDF will be based on
5. ID of above Google Doc template (e.g. https://drive.google.com/drive/folders/XXXXXXXX_XXX?usp=drive_link)
6. All Google permission prompts accepted by the user

## Instructions

### In Google Sheets sheet
1. Create the following column headers:
  - ID (to show the ID in the file name)
  - Name (to show the Name in the file name)
  - Status (to insert the generated PDF's link)
2. You can insert as much other data as you want

### In Google Docs template
Make a placeholder reference to exact the column header name you want to parse, do this for every column that you want to include in the PDF

Example: 
**Name** in Google Sheets sheet
**{{Name}}** in Google Doc template

### In Apps Script
This script will only work if it has all the relevant permissions. 

In case you want to change them,
1. In Google Sheets, go to **Extensions** > **Apps Script**
2. Go to **Project Settings** > Tick :ballot_box_with_check: "Show "appsscript.json" manifest file in editor"
3. Insert the relevant permissions in  `appsscript.json`

``` json
  "oauthScopes": [
    "https://www.googleapis.com/auth/drive",
    "https://www.googleapis.com/auth/drive.readonly",
    "https://www.googleapis.com/auth/documents",
    "https://www.googleapis.com/auth/spreadsheets",
    "https://www.googleapis.com/auth/script.container.ui",
    "https://www.googleapis.com/auth/userinfo.email"
  ]
```


