erDiagram
    Users {
        string _id PK
        string username
        string passwordHash
        string email
        string role
        datetime createdDate
    }

    Cases {
        string _id PK
        string caseName
        text description
        datetime createdDate
        string status
        Document[] documents
        ReviewAssignment[] reviewAssignments
    }

    Documents {
        string documentID
        string filePath
        string fileName
        string fileType
        datetime uploadDate
        string uploadedBy FK
        Metadata metadata
        string[] tags
    }

    Metadata {
        string author
        datetime creationDate
    }

    ReviewAssignments {
        string assignmentID
        string documentID
        string assignedTo FK
        datetime assignedDate
        string reviewStatus
        text comments
    }

    AuditLog {
        string _id PK
        string action
        string userID FK
        string documentID FK
        datetime timestamp
        text details
    }

    Users ||--o{ Documents : uploadedBy
    Cases ||--o{ Documents : documents
    Cases ||--o{ ReviewAssignments : reviewAssignments
    Users ||--o{ ReviewAssignments : assignedTo
    Users ||--o{ AuditLog : userID
    Documents ||--o{ AuditLog : documentID
