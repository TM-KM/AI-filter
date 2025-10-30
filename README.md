# AI-filter
AI 필터링(차별)
```mermaid
graph TD
    A[1_사용자_인터페이스_Frontend] --> B{2_API_서버_Backend}
    B --> C[3_기반_LLM_Base_LLM_호출]
    C --> D{4_LLM_답변_생성_원본}
    D --> E[5_편향성_탐지_모듈_Detection]
    E --> F{6_편향성_지수_측정}
    F -- High_Bias --> G[7_편향성_교정_모듈_Correction]
    F -- Low_Bias --> H[8_최종_출력_교정_불필요]
    G --> H
    H --> I[9_최종_결과_출력_Frontend]
    I -- 투명성_제공 --> J[결과_비교_및_편향성_지수_시각화]

    subgraph BiasFilterLayer [Bias Filter Layer]
        E
        F
        G
    end
    style BiasFilterLayer fill:#f9f,stroke:#333,stroke-width:2px,stroke-dasharray: 5 5

    classDef core fill:#CCEEFF,stroke:#333
    classDef llm fill:#FFCCAA,stroke:#333
    classDef process fill:#DDFFDD,stroke:#333

    class E,G core
    class C llm
    class J process
