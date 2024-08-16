graph TD
    A[Mobile App] --> API[API Gateway]

    subgraph Microservices
        API --> B[Authentication Service]
        API --> C[Questionnaire Service]
        API --> D[Results Display Service]
        API --> E[Upload-to-Server Service]
    end

    subgraph Message Bus
        F((Message Queue))
    end
    
    B <--> F
    C <--> F
    D <--> F
    E <--> F

    E -->|Upload Files| G[Centralized Data Repository]
    G -->|Notify Completion| F

    B -->|Auth UI Component| A
    C -->|Questionnaire UI Component| A
    D -->|Results UI Component| A
    E -->|Upload Status UI Component| A
