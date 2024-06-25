erDiagram
    Users {
        int UserID PK
        string Username
        string PasswordHash
        string Email
        string Role
        datetime CreatedDate
    }

    Cases {
        int CaseID PK
        string CaseName
        text Description
        datetime CreatedDate
        string Status
    }

    Documents {
        int DocumentID PK
        int CaseID FK
        string FilePath
        string FileName
        string FileType
        datetime UploadDate
        int UploadedBy FK
    }

    DocumentMetadata {
        int MetadataID PK
        int DocumentID FK
        string Key
        string Value
    }

    Tags {
        int TagID PK
        string TagName
    }

    DocumentTags {
        int DocumentID FK
        int TagID FK
    }

    ReviewAssignments {
        int AssignmentID PK
        int CaseID FK
        int DocumentID FK
        int AssignedTo FK
        datetime AssignedDate
        string ReviewStatus
        text Comments
    }

    AuditLog {
        int LogID PK
        string Action
        int UserID FK
        int DocumentID FK
        datetime Timestamp
        text Details
    }

    Users ||--o{ Documents : "UploadedBy"
    Cases ||--o{ Documents : "CaseID"
    Documents ||--o{ DocumentMetadata : "DocumentID"
    Documents ||--o{ DocumentTags : "DocumentID"
    Tags ||--o{ DocumentTags : "TagID"
    Cases ||--o{ ReviewAssignments : "CaseID"
    Documents ||--o{ ReviewAssignments : "DocumentID"
    Users ||--o{ ReviewAssignments : "AssignedTo"
    Users ||--o{ AuditLog : "UserID"
    Documents ||--o{ AuditLog : "DocumentID"