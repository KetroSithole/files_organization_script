# File Organization Script

This PowerShell script automatically organizes files from your Desktop into categorized folders based on file type. It creates a main folder called `file_organization` on your Desktop and organizes PDF, Excel, Text, and Image files into their respective subfolders.

## Features

- Dynamic Folder Creation: The script dynamically identifies the user's Desktop path and creates a `file_organization` folder if it doesn't already exist.
- Subfolder Organization: The script creates subfolders for PDFs, Excel files, Text files, and Image files.
- File Sorting: Files are automatically moved to their respective subfolders based on their file extensions (PDF, Excel, Text, Image).
- File Type Support: Supported file types include:
  - `.pdf` (PDF files)
  - `.xlsx` (Excel files)
  - `.txt` (Text files)
  - `.jpg`, `.png` (Image files)

## Usage

### Prerequisites:
- PowerShell 5.1 or later

### Script Workflow:
1. **Main Folder Creation**: The script checks if the `file_organization` folder exists on the Desktop and creates it if necessary.
2. **Subfolder Creation**: It creates subfolders under `file_organization` for PDFs, Excel files, Text files, and Images.
3. **File Sorting**: All files on the Desktop are reviewed and moved into their appropriate subfolder based on their extension.

### File Types Handled:
- **PDF files**: Moved to `file_organization\PDFs`
- **Excel files**: Moved to `file_organization\ExcelFiles`
- **Text files**: Moved to `file_organization\TextFiles`
- **Image files (PNG, JPG)**: Moved to `file_organization\Images`

## Running the Script

To run the script, follow these steps:

1. Save the script as `sort_files.ps1` on your system.
2. Open **PowerShell** as an Administrator.
3. Navigate to the folder where the script is saved.
4. Run the script by typing `.\sort_files.ps1`.

### Scheduling the Script

To automatically run the script on a daily basis, you can schedule it using **Task Scheduler**:

1. Open **Task Scheduler** and click on **Create Basic Task**.
2. Name the task and set the trigger to **Daily**.
3. Under **Action**, choose **Start a Program**, and select the `sort_files.ps1` script.
4. Finish the setup and let the task run automatically each day.

## Conclusion

This script offers a simple and effective solution to keep your desktop organized by categorizing files based on type. It is ideal for automating file management tasks and improving productivity.