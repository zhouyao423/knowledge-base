# download-attachment

Download files from URLs to attachments folder and organize them with descriptive names.

## Usage
```
/download-attachment <url1> [url2] [url3...]
```

## Examples
```
/download-attachment https://example.com/document.pdf
/download-attachment https://site.com/image.png https://site.com/report.pdf
```

## Implementation

You are tasked with downloading files from URLs and organizing them in the Obsidian vault attachments folder.

### Step 1: Parse URLs
Extract the URL(s) from the user's input. Handle multiple URLs if provided.

### Step 2: Download Files
For each URL:
```bash
# Create temp filename based on URL
# Use wget or curl to download
wget -O "05_Attachments/[filename]" "[url]"
# or
curl -L "[url]" -o "05_Attachments/[filename]"
```

### Step 3: Verify Downloads
Check that files were downloaded successfully:
```bash
ls -la "05_Attachments/"
```

### Step 4: Organize Files
After downloading, run the organize-attachments command to rename files with descriptive names:

For PDFs:
- Extract text with `pdftotext`
- Analyze content for meaningful title

For Images:
- Use `mcp__gemini-vision__analyze_image` or `mcp__gemini-vision__analyze_multiple`
- Generate descriptive filename based on content

### Step 5: Move to Organized
Move renamed files to `05_Attachments/Organized/` with descriptive names

### Step 6: Update Index
Add entries to `05_Attachments/00_Index.md`

### Step 7: Commit Changes
```bash
git add -A
git commit -m "Download and organize attachments from URLs"
git push
```

## Important Notes

1. **File Naming**: 
   - Initial download: Use URL filename or generate from URL
   - After analysis: Rename with descriptive title

2. **Supported Types**:
   - Images: .png, .jpg, .jpeg, .gif, .webp
   - Documents: .pdf, .doc, .docx
   - Text: .txt, .md
   - Data: .csv, .xlsx

3. **Error Handling**:
   - Check if URL is accessible
   - Verify file downloaded correctly
   - Handle download failures gracefully

4. **Organization**:
   - Downloaded files go to `05_Attachments/`
   - After renaming, move to `05_Attachments/Organized/`
   - Update links across vault if needed

## Workflow

1. Download file(s) from provided URL(s)
2. Identify file type and analyze content
3. Generate descriptive filename
4. Move to Organized folder
5. Update index and references
6. Commit and push changes

## Tips

- For multiple URLs, process them in batch for efficiency
- Use Gemini Vision for batch image analysis (up to 3 at once)
- Extract meaningful context from PDFs before renaming
- Preserve original file extensions
- Keep filenames concise but descriptive (max 60 chars)