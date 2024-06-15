# Google-Sheet-Rows-to-PDF
Google Apps Script to generate PDF/s from a single or multiple Google Sheet row/s. 

🔗 [Link to Drive folder of all relevant files](https://drive.google.com/drive/folders/1WgX4NAEuIvpV3iiiObg1UrrnkOUrnkGR?usp=sharing)

This script works by:
- Getting a user's input on which row/s they want to generate a PDF from,
- parsing the row's by matching the Sheets data with the `{{placeholder}}` set in the template document,
- converting the row values into the template document,
- generating a PDF from the template document.

⤵️ [Features](##Features)
⤵️ [Running the Script](##running-the-script)
⤵️ [Further details](##further-details)

## Features 
- Skips a row if a PDF has already been generated 
- Sheets UI to:
    - prompt input from the user to configure single or multiple PDF generation
    - prompt input from the user to enter number of rows to be generated
    - show progress of PDF generation
    - show PDF link/s
    - show if row/s have been skipped
    - show errors 

## Running the Script
This script requires a bit of setup before running.

### Prerequisites
1. Google Sheets data with at least the following column headers:
  - ID (to show the ID in the file name)
  - Name (to show the Name in the file name)
  - Status (to insert the generated PDF's link)
2. Google Drive folder for where the PDFs will be contained - **user must have edit permissions**
3. ID of above Google Drive folder (e.g. https://drive.google.com/drive/folders/XXXXXXXX_XXXXXX)
4. Google Doc template that the PDF will be based on
5. ID of above Google Doc template (e.g. https://docs.google.com/document/d/XXXXXXXX_XXXXXX/edit?usp=drive_link)
6. All Google permission prompts accepted by the user

### Setup
- Duplicate the entire folder
- In the Demo Data spreadsheet, click `Extensions` in the header > click `Apps Script`
- Change `TEMPLATE_FILE_ID` to the ID of your Doc template
- Change `FOLDER_ID` to the ID of your PDFs folder
- Save the project

### Running the script
Whoo! That was a lot of setup. Now to see if it works.

In the header of the spreadsheet, click `Generate PDFs`. 
It will prompt you to accept the permissions set by the script, I promise the code is safe. You can accept this prompt.
![339363299-a511c099-5a16-4610-9589-cdaad221baba](https://github.com/nelrob/Google-Sheet-Rows-to-PDF/assets/71628453/6a80cf1e-c258-45fd-ab12-584096a3feb1)

Choose if you want to generate single or multiple PDFs, and enter the rows you'd like to be generated.

The script takes a few seconds to run, you'll know it works when the `Generated` column is populated with the hyperlinks to the newly generated PDFs!
![image](https://github.com/nelrob/Google-Sheet-Rows-to-PDF/assets/71628453/bb26ec95-85bd-40ac-8a14-60a9ecd71049)

## Further details

### In Google Sheets sheet
1. It needs at least the following column headers:
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
2. Go to **Project Settings** > Tick :ballot_box_with_check: Show "appsscript.json" manifest file in editor
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
