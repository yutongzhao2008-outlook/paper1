graph TD
    A[Start] --> B{Prompting Strategy Selection}
    B -->|ZERO - shot| C[Input Test Set Data]
    B -->|90SHOTS| D[Input Training Set + Test Set]
    B -->|Decomposed| E[Input Training Set + Test Set]
    
    %% Zero - shot Process
    C --> F[Execute Pre - defined Rule Classification]
    F --> G[Generate Classification Result File]
    G --> H[Calculate Evaluation Metrics]
    H --> I[Output Evaluation Chart]
    
    %% 90SHOTS Process
    D --> J[Analyze Training Set Patterns]
    J --> K[Build Softmax Classifier]
    K --> L[Test Set Prediction]
    L --> M[Generate Classification Result File]
    M --> N[Calculate Evaluation Metrics]
    N --> O[Output Evaluation Chart]
    
    %% Decomposed Process
    E --> P[Data Pre - processing]
    P --> Q[Feature Engineering]
    Q --> R[Model Iterative Training]
    R --> S{Logistic Regression, Decision Tree, Random Forest, Gradient Boosting, SVM, KNN accuracy > 0.95}
    S -->|No| R
    S -->|Yes| T[Final Model Prediction]
    T --> U[Generate Classification Result File]
    U --> V[Cross - validation Evaluation]
    V --> W[Output Evaluation Chart]
    
    classDef strategy fill:#f9f,stroke:#333;
    classDef process fill:#bbf,stroke:#333;
    classDef decision fill:#ff9,stroke:#333;
    class B,S decision;
    class C,D,E strategy;
    class F,G,H,J,K,L,M,N,O,P,Q,R,T,U,V,W process;
    
    style A fill:#4CAF50,stroke:#388E3C
    style I fill:#FF5722,stroke:#E64A19
    style O fill:#FF5722,stroke:#E64A19
    style W fill:#FF5722,stroke:#E64A19