sequenceDiagram
    participant DS as Data Science Team
    participant Model as Diabetes Prediction Model
    participant SD as Software Development Team
    participant App as Mobile-First Web Application

    Note over DS,SD: Initial Planning
    DS->>SD: Discuss project requirements
    DS->>SD: Define data and model requirements

    Note over SD: Development Phase
    SD->>App: Develop frontend and backend

    Note over DS: Data Preparation Phase
    DS->>DS: Collect and preprocess data

    Note over DS: Model Validation Phase
    DS->>Model: Analyze Model outputs
    DS->>Model: Develop, train, and validate model

    Note over DS,SD: DataSci/SoftDev Integration Phase
    DS->>SD: Provide model API specifications
    SD->>App: Develop model API
    App->>Model: Send data for prediction
    Model-->>App: Return prediction results

    Note over SD: Testing Phase
    SD->>App: Perform unit and integration testing
    SD->>DS: Collaborate on resolving data/model issues

    Note over SD,DS: Deployment Phase
    SD->>App: Deploy application
    App->>Model: Operationalize prediction model

    Note over DS,SD: Monitoring and Maintenance
    App->>DS: Provide user data and feedback
    DS->>Model: Update and retrain model