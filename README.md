# File Organization Script

This PowerShell script automatically organizes files from your Desktop into categorized folders based on file type. It creates a main folder called `file_organization` on your Desktop and organizes PDF, Excel, Text, and Image files into their respective subfolders.

## Features

- **Dynamic Folder Creation**: The script dynamically identifies the user's Desktop path and creates a `file_organization` folder if it doesn't already exist.
- **Subfolder Organization**: The script creates subfolders for PDFs, Excel files, Text files, and Image files.
- **File Sorting**: Files are automatically moved to their respective subfolders based on their file extensions (PDF, Excel, Text, Image).
- **File Type Support**: Supported file types include:
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

## Script Details

```powershell
# Define the desktop path dynamically
$desktopPath = [System.Environment]::GetFolderPath('Desktop')
$mainFolderPath = "$desktopPath\file_organization"

# Subfolder paths with _automated_folder suffix
$pdfFolder = "$mainFolderPath\PDFs"
$excelFolder = "$mainFolderPath\ExcelFiles"
$textFolder = "$mainFolderPath\TextFiles"
$imageFolder = "$mainFolderPath\Images"  # For image files like PNG, JPG, etc.

# Create the main folder if it doesn't exist
if (-not (Test-Path -Path $mainFolderPath)) {
    New-Item -Path $mainFolderPath -ItemType Directory
    Write-Host "Main folder created at: $mainFolderPath"
} else {
    Write-Host "Main folder already exists at: $mainFolderPath"
}

# Create subfolders for PDFs, Excel files, Text files, and Images with _automated_folder suffix
$subfolders = @($pdfFolder, $excelFolder, $textFolder, $imageFolder)
foreach ($folder in $subfolders) {
    if (-not (Test-Path -Path $folder)) {
        New-Item -Path $folder -ItemType Directory
        Write-Host "Folder created: $folder"
    } else {
        Write-Host "Folder already exists: $folder"
    }
}

# Define the folder where you want to organize the files (e.g., your Desktop)
$sourceFolder = $desktopPath

# Get all files in the source folder (Desktop)
$files = Get-ChildItem -Path $sourceFolder -File

# Organize the files into their respective folders based on file type
foreach ($file in $files) {
    # Check the file type and move to the respective folder
    switch ($file.Extension.ToLower()) {
        ".pdf" {
            # Move PDF files if folder exists
            if (Test-Path -Path $pdfFolder) {
                Move-Item -Path $file.FullName -Destination $pdfFolder
                Write-Host "Moved PDF file: $($file.Name)"
            } else {
                Write-Host "PDF folder does not exist: $pdfFolder"
            }
        }
        ".xlsx" {
            # Move Excel files if folder exists
            if (Test-Path -Path $excelFolder) {
                Move-Item -Path $file.FullName -Destination $excelFolder
                Write-Host "Moved Excel file: $($file.Name)"
            } else {
                Write-Host "Excel folder does not exist: $excelFolder"
            }
        }
        ".txt" {
            # Move Text files if folder exists
            if (Test-Path -Path $textFolder) {
                Move-Item -Path $file.FullName -Destination $textFolder
                Write-Host "Moved Text file: $($file.Name)"
            } else {
                Write-Host "Text folder does not exist: $textFolder"
            }
        }
        ".jpg" {
            # Move JPG image files if folder exists
            if (Test-Path -Path $imageFolder) {
                Move-Item -Path $file.FullName -Destination $imageFolder
                Write-Host "Moved JPG image file: $($file.Name)"
            } else {
                Write-Host "Image folder does not exist: $imageFolder"
            }
        }
        ".png" {
            # Move PNG image files if folder exists
            if (Test-Path -Path $imageFolder) {
                Move-Item -Path $file.FullName -Destination $imageFolder
                Write-Host "Moved PNG image file: $($file.Name)"
            } else {
                Write-Host "Image folder does not exist: $imageFolder"
            }
        }
        Default {
            Write-Host "No action for file: $($file.Name)"
        }
    }
}
```

## Conclusion

This script offers a simple and effective solution to keep your desktop organized by categorizing files based on type. It is ideal for automating file management tasks and improving productivity.
