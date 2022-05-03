http://woshub.com/powershell-commands-history/#:~:text=Using%20the%20F8%20key%2C%20you,in%20history%2C%20press%20F8%20again.


`Get-History | Format-List -Property *`

`Get-History`


`notepad (Get-PSReadLineOption | select -ExpandProperty HistorySavePath`

`Get-PSReadlineOption | select HistoryNoDuplicates, MaximumHistoryCount, HistorySearchCursorMovesToEnd, HistorySearchCaseSensitive, HistorySavePath, HistorySaveStyle`
-   **HistoryNoDuplicates** – determines whether the same commands have to be saved;
-   **MaximumHistoryCount** – the maximum number of the stored commands (by default the last 4096 commands are saved);
-   **HistorySearchCursorMovesToEnd** — determines whether you have to go to the end of the command when searching;
-   **HistorySearchCaseSensitive** – determines whether search is case sensitive (PS command history is not case sensitive by default);
-   **HistorySavePath** – shows the path to the file in which the command is stored;
-   **HistorySaveStyle** – determines the peculiarities of saving commands:
    -   _**SaveIncrementally**_ — the commands are saved after they are run (by default);
    -   _**SaveAtExit** —_ the history is saved when the PowerShell console is closed;
    -   _**SaveNothing**_ — disable saving command history.
