This document is for **public** use to aid in localizing the game.

# **Language Files**
This section explains the localization file structure, location and format.

#### **Location**
You can find language files in the games `data/languages/` folder. 
Each subfolder is a specific directory for every language, which is the subfolders name.

#### **Format**
All language files are **Tab Separated Values** (.tsv) files which behave similarly to **Comma Separated Values** (.csv) files but are separated by tabs instead of commas.

#### **Structure**
Each language file is made up of any amount of lines containing either two or three columns per line. For example:

`PANEL_START	Start`
`PANEL_EXIT	Exit	-2`
`PANEL_INFO	Today is {{0}}`

In this case, `SOME_KEY` is an internal key used in the game to represent a value that is retrieved via localization. You should not change this.

The `Value` column is direct text that is displayed in the game. You should change this to an according value in your language.
Some entries might use parameters, which are text inserted by the game. Parameters are specified by `{{index}}` and should not be modified, only moved around in-case the languages grammar requires it.

The third and **optional** column is a positive or negative number indicating a font size offset. You can specify this if the localized value is too long in your language to make it smaller.

<div style="page-break-after: always;"></div>

# **Localization**
After reading and understanding the structure of the language file, you can begin localizing the game to your language like so:
1. Copy the entire `English` folder found in the languages directory.
2. Rename it to your language, for example: `German`.
3. Edit each individual file in your renamed directory, replacing the `Value` column to your localized values and specifying a font offset if needed.

# **Testing**
Make sure to save your files and start the game.
Selecting your language in the game settings should apply it to all text elements and you can observe if everything is displayed correctly or needs changes.

<div style="page-break-after: always;"></div>

# **Debugging**
If something does not work correctly, you should check the `logs` folder in your game directory for any errors and warnings.

#### **Empty Files**
If an empty language file exists, when the game starts it will print the following:

`[LocalizationManager] Skipping language file {file} for language {language} because it is empty`

#### **Incorrect Entries**
If an entry (a single line in a language file) has less than two tab-separated values, it will fail with the following:

`[LocalizationManager] Skipping line {lineNumber} for language {language} file {file} because it failed to parse`

If a specified font size column is not a valid number, it will fail with the following:

`[LocalizationManager] Skipping font size offset for file {file} and line {lineNumber} and language {language} because it failed to parse`

#### **Incorrect Files**
If a corrupt language file exists (this should never happen), the game starts will print the following:

`[LocalizationManager] Skipping language file {file} for language {language} because it is corrupt`

#### **Loaded Languages**
Once the game starts finishes loading a language, it will print the following:

`[LocalizationManager] Loaded language {language} with {entriesCount} entries from {filesCount} files`