```mermaid
info
flowchart TB

    subgraph WIN["Windows 11 (Host)"]
        DD["Docker Desktop\n- Docker Engine\n- Docker Compose"]
        VS["Visual Studio Code (Windows)\n- Remote WSL Extension\n- VS Code Server installed in WSL"]
    end

    subgraph WSL["WSL2 Virtualization Layer"]
    end

    subgraph ALMA["AlmaLinux 10 (WSL2)"]
        SHELL["Linux Native Environment\n- bash / zsh\n- dnf package manager"]
        VSCODE["VS Code Server\n/usr/bin/code available\n\'code .\' launches VS Code"]
        DOCKERCLI["Docker CLI\ncontrols Docker Desktop"]
    end

    WIN --> WSL
    WSL --> ALMA

    ALMA --> DOCKERCLI --> DD
    ALMA --> VSCODE --> VS
```
