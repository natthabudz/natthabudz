flowchart LR
    A["Start"] --> B["Data Collection"]

    subgraph subGraph0["1. Data Collection"]
        B --> C{"Point of Sale or Post Sale?"}
        C -->|Point of Sale| D["Customer Data and Transaction"]
        C -->|Post Sale| E["Call Back and Welcome Call"]
        D --> F{"Digital or Paper Form?"}
        F -->|Digital| G["Microsoft Forms"]
        F -->|Paper| H["Scan & OCR via Power Automate"]
        G & H --> I["Store in OneDrive"]
        E --> J["Record Conversation"]
        J --> K["Store Audio Files - OneDrive"]
    end

    subgraph subGraph1["2. Document and Audio Verification"]
        I --> L["Document Verification"]
        L --> M["ML Signature Check - Azure ML"]
        L --> N["AI Data Accuracy Check - Power Automate"]
        K --> O["Audio File Processing"]
        O --> P["Speech-to-Text - Azure Speech Service"]
        P --> Q["Conversation Analysis - Azure Cognitive Services"]
        Q --> R["Detect Inappropriate Speech - Azure Anomaly Detector"]
    end

    subgraph subGraph2["3. Sales Behavior Analysis"]
        M & N & R --> S["Deep Learning Analysis - Azure ML"]
        S --> T["Anomaly Detection - Azure Anomaly Detector"]
    end

    subgraph subGraph3["4. Alerts and Clarifications"]
        T --> U{"Issues Detected?"}
        U -->|Yes| V["Generate Clarification Email - Generative AI"]
        U -->|Yes| W["Send Automated Alert - Power Automate"]
        V --> X["Send Email via Outlook"]
    end

    subgraph subGraph4["5. Reporting and Analysis"]
        U -->|No| Y["Update Dashboard - Power BI"]
        W & X --> Y
        Y --> Z["Generate Reports - Power BI"]
    end

    Z --> AA["End"]
