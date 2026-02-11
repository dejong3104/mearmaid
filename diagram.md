flowchart TB

    %% ============================
    %% Nodes
    %% ============================

    subgraph WIN[Windows 11 (Host)]
        DD[Docker Desktop<br/>- Docker Engine<br/>- Docker Compose]
        VS[Visual Studio Code (Windows)<br/>- Remote WSL Extension<br/>- VS Code Server installed in WSL]
    end

    subgraph WSL[WSL2 Virtualization Layer]
    end

    subgraph ALMA[AlmaLinux 10 (WSL2)]
        SHELL[Linux Native Environment<br/>- bash / zsh<br/>- dnf package manager]
        VSCODE[/usr/bin/code available<br/>"code ." launches VS Code]
        DOCKERCLI[Docker CLI<br/>controls Docker Desktop]
    end

    %% ============================
    %% Connections
    %% ============================

    WIN --> WSL
    WSL --> ALMA

    ALMA --> DOCKERCLI --> DD
    ALMA --> VSCODE --> VS

    %% ============================
    %% Styles (Color Coding)
    %% ============================

    %% Windows Host = Blue
    style WIN fill:#d0e4ff,stroke:#4a90e2,stroke-width:2px

    %% Docker Desktop = Light Yellow
    style DD fill:#fff4c2,stroke:#d1b000,stroke-width:1.5px

    %% VS Code = Light Purple
    style VS fill:#e8d9ff,stroke:#9b59b6,stroke-width:1.5px

    %% WSL Layer = Gray
    style WSL fill:#f0f0f0,stroke:#999,stroke-width:1px

    %% AlmaLinux = Light Green
    style ALMA fill:#d9f7d9,stroke:#27ae60,stroke-width:2px

    %% AlmaLinux components
    style SHELL fill:#ffffff,stroke:#27ae60,stroke-width:1px
    style VSCODE fill:#ffffff,stroke:#9b59b6,stroke-width:1px
    style DOCKERCLI fill:#ffffff,stroke:#d1b000,stroke-width:1px
