flowchart TD
    A>1. Problem Definition and Requirements Gathering]
    B[(2. Data Collection and ETL from the CDC)]
    C[(3. Data Preparation: Cleanliness and Statistical Normalization)]
    D[\4. Exploratory Data Analysis\]
    E[\5. Model Development\]
    F[\6. Model Validation and Insight\]
    G{{7. Deployment and Integration}}
    H{{8. Monitoring and Maintenance}}
    I{{9. Analysis and Reporting}}
    J>10. Feedback and Critial Evaluation]

    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
    F --> D
    F --> G
    G --> H
    H --> I
    I --> J
    J --> B