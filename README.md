# AI-filter
AI 필터링(차별)
```mermaid
graph TD
    A[사용자 인터페이스_Frontend] --> B{API 서버_Backend}
    B --> C[기반_LLM Base_LLM 호출]
    C --> D{LLM 답변 생성 원본}
    D --> E[편향성 탐지 모듈_Detection]
    E --> F{편향성 지수 측정}
    F -- High_Bias --> G[편향성 교정 모듈_Correction]
    F -- Low_Bias --> H[최종 출력 교정 불필요]
    G --> H
    H --> I[최종 결과 출력_Frontend]
    I -- 투명성_제공 --> J[결과 비교 및 편향성 지수 시각화]

    subgraph BiasFilterLayer [편향된 결과 필터 레이어]
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
