<!--
{
  "title": "How to add \"Open with VSCodium\" for Windows",
  "time": "2025-02-06T00:02:00.000Z",
  "description": "How to add \"Open with VSCodium\" for Windows If you're a developer using VSCodium on Windows, you might want a convenient way to open directories directly from File Explorer. This guide explains how to add \"Open with VSCodium\" to the context menu by modifying the Windows registry. We will cover..."
}
-->

![open_vscodium.webp](/images/uploads/open_vscodium.webp)
# How to add "Open with VSCodium" for Windows
If you're a developer using VSCodium on Windows, you might want a convenient way to open directories directly from File Explorer. This guide explains how to add "Open with VSCodium" to the context menu by modifying the Windows registry.

We will cover how to:

1. Add the option when right-clicking a folder name.
2. Add the option when right-clicking an empty space inside a folder.

## Adding Registry Entries
The following registry commands will help you achieve these functionalities.

### 1. Add "Open with VSCodium" When Right-Clicking a Folder
This configuration allows you to open any folder by right-clicking directly on its name.

**Command:**
```
reg add "HKEY_CLASSES_ROOT\Directory\shell\Open with VSCodium\command" /d "\"C:\Users\your-username\AppData\Local\Programs\VSCodium\VSCodium.exe\" \"%1\"" /f
```
**Explanation:**
- HKEY_CLASSES_ROOT\Directory\shell\Open with VSCodium\command: Specifies the registry path to add the context menu option for folders.
- %1: Passes the path of the folder you right-clicked.
- Adjust C:\Users\your-username\AppData\Local\Programs\VSCodium\VSCodium.exe to match the location of your VSCodium installation.

### 2. Add "Open with VSCodium" When Right-Clicking in an Empty Space
This setup allows you to right-click in a blank area inside a directory and open that directory in VSCodium.

#### Step 1: Create the Main Entry
**Command:**
```
reg add "HKEY_CLASSES_ROOT\Directory\shell\Open with VSCodium\command" /d "\"C:\Users\your-username\AppData\Local\Programs\VSCodium\VSCodium.exe\" \"%1\"" /f
```
#### Step 2: Add Icon
**Command:**
```
reg add "HKEY_CLASSES_ROOT\Directory\Background\shell\Open with VSCodium" /v "Icon" /d "\"C:\Users\your-username\AppData\Local\Programs\VSCodium\VSCodium.exe\"" /f
```
#### Step 3: Set the Command Path
**Command:**
```
reg add "HKEY_CLASSES_ROOT\Directory\Background\shell\Open with VSCodium\command" /ve /d "\"C:\Users\your-username\AppData\Local\Programs\VSCodium\VSCodium.exe\" \"%V\"" /f
```
**Explanation:**

- HKEY_CLASSES_ROOT\Directory\Background\shell\Open with VSCodium: Adds the option when right-clicking on empty space inside a folder.
- %V: Refers to the current directory path.

## Using Both Options Together
To have both options available—for folders and empty spaces—run all three commands together:

```
reg add "HKEY_CLASSES_ROOT\Directory\shell\Open with VSCodium\command" /d "\"C:\Users\your-username\AppData\Local\Programs\VSCodium\VSCodium.exe\" \"%1\"" /f
reg add "HKEY_CLASSES_ROOT\Directory\Background\shell\Open with VSCodium" /ve /d "Open with VSCodium" /f
reg add "HKEY_CLASSES_ROOT\Directory\Background\shell\Open with VSCodium" /v "Icon" /d "\"C:\Users\your-username\AppData\Local\Programs\VSCodium\VSCodium.exe\"" /f
reg add "HKEY_CLASSES_ROOT\Directory\Background\shell\Open with VSCodium\command" /ve /d "\"C:\Users\your-username\AppData\Local\Programs\VSCodium\VSCodium.exe\" \"%V\"" /f
```
## Important Notes:
- Run these commands in an elevated command prompt (as Administrator).
- Double-check the path to your VSCodium installation.
- If you make mistakes, you can remove the entries by deleting the corresponding registry keys.

With these changes, you can seamlessly open directories in VSCodium right from File Explorer, boosting your workflow efficiency.