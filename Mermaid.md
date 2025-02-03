graph TD
    A[开始] --> B{提示策略选择}
    B -->|ZERO-shot| C[输入测试集数据]
    B -->|90SHOTS| D[输入训练集+测试集]
    B -->|Decomposed| E[输入训练集+测试集]
    
    %% Zero-shot流程
    C --> F[执行预定义规则分类]
    F --> G[生成分类结果文件]
    G --> H[评估指标计算]
    H --> I[输出评估图表]
    
    %% 90SHOTS流程
    D --> J[分析训练集模式]
    J --> K[构建Softmax分类器]
    K --> L[测试集预测]
    L --> M[生成分类结果文件]
    M --> N[评估指标计算]
    N --> O[输出评估图表]
    
    %% Decomposed流程
    E --> P[数据预处理]
    P --> Q[特征工程]
    Q --> R[模型迭代训练]
    R --> S{(Logistic Regression,Decision Tree,Random Forest,Gradient Boosting,SVM,KNN) accuracy > 0.95}
    S -->|否| R
    S -->|是| T[最终模型预测]
    T --> U[生成分类结果文件]
    U --> V[交叉验证评估]
    V --> W[输出评估图表]
    
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