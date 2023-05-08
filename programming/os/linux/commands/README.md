# Linux Commands

1. `Fork Bomb`

    ```bash
    :(){ :|:& };:
    ```

    The command creates a function called ":" that recursively calls itself twice, creating an exponentially growing number of child processes in a very short period of time. The "&" symbol sends each of these child processes to the background, allowing the parent process to continue creating more and more child processes until all system resources are exhausted, causing the system to crash or become unresponsive.

    In other words, this code is designed to overload and crash the system it is executed on.

2.
