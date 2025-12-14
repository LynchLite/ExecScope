


![App Screenshot](https://i.imgur.com/iB8ItL7.png)


# ExecScope - eXeTools.org

ExecScope is a portable, user-mode sandbox for Windows designed to perform rapid behavioral analysis of executable files. It provides immediate insight into the actions of a binary—including file system modifications, registry persistence, network connections, and process spawning—without requiring kernel-mode drivers or complex installation procedures.


## Acknowledgements

 - [eXeTools WebSite](https://exetools.org)
 - [Download ExecScope](https://exetools.org/details/17)


# Features
### Dynamic Analysis
* **File System Monitoring**: Tracks file creation, modification, and deletion in critical directories (`%TEMP%`, `%APPDATA%`, and local paths).
*   **Registry Monitoring**: Detects changes to persistence keys (Run keys) and other system configurations.
*   **Process Tracking**: Monitors the creation of child processes and identifies shell spawning (cmd.exe, powershell.exe).
*   **Network Monitoring**: Snapshots active TCP connections to detect C2 callbacks.
### Static Analysis
*   **PE Header Parsing**: Analyzes the Import Address Table (IAT) to detect suspicious API usage (e.g., `RegCreateKey`, `VirtualAlloc`, `InternetOpen`) before execution.

### Intelligence
*   **Risk Scoring**: A heuristic engine assigns a risk score (0-100) based on observed behaviors.
*   **Classification**: Automatically tags samples as Low Risk, Suspicious, or Malicious.
*   **Reporting**: Outputs detailed `.txt` reports for analysts and structured `.json` reports for SIEM integration.

## Usage
ExecScope uses an interactive Command Line Interface (CLI).

1.  Start the application.
    ```text
    ExecScope>
    ```
2.  Select a target file.
    ```text
    ExecScope> open C:\Path\To\Sample.exe
    ```
    *(Or simply type `open` to use the file picker dialog)*

3.  (Optional) Set command-line arguments for the target.
    ```text
    ExecScope> args -install -silent
    ```

4.  Run the analysis.
    ```text
    ExecScope> run
    ```

5.  Review the output on screen or open the generated `report_[PID].txt`.
## Disclaimer

ExecScope executes the target file on the host system. **It does not provide virtualization or isolation.**
*   **DO NOT** run malicious files on your personal machine.
*   **ALWAYS** use a Virtual Machine (VM) or a dedicated disposable environment when analyzing malware.
*   The authors are not responsible for any damage caused by the execution of malicious software using this tool.

## License

MIT License

