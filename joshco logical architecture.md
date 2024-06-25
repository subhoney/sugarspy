graph TD;
    A(((JoshCo))) -->|SFTP/Aspera Upload| B[Ingress Point, Azure Front Door]
    B -->|HTTPS| C{{Document Storage, Azure Blobs}}
    C -->|Geo-redundant Storage| C
    C -->|Trigger| D[Metadata Extraction, Azure Functions]
    D -->E[(Azure SQL DB)]
    D -->|Geo-redundant Data Storage| D
    E -->|HTTPS Access| F[Egress Point, Azure Front Door]
    F -->|SFTP/Aspera Download| G(((Client Devices)))
    
    subgraph Security and Monitoring
        H[Azure Key Vault]
        I[Azure Monitor]
        J[Azure Security Center]
    end
    
    C --- H
    D --- I
    F --- J