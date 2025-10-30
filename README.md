# AI-filter
AI 필터링(차별)
graph TD
    A[1. 사용자 인터페이스 (Frontend)] --> B{2. API 서버 (Backend)}
    B --> C[3. 기반 LLM (Base LLM) 호출]
    C --> D{4. LLM 답변 생성 (원본)}
    D --> E[5. 편향성 탐지 모듈 (Detection)]
    E --> F{6. 편향성 지수 측정}
    F -- 지수 높음 (High Bias) --> G[7. 편향성 교정 모듈 (Correction)]
    F -- 지수 낮음 (Low Bias) --> H[8. 최종 출력 (교정 불필요)]
    G --> H
    H --> I[9. 최종 결과 출력 (Frontend)]
    I -- 투명성 제공 --> J[결과 비교 및 편향성 지수 시각화]

    %% Bias Filter Layer 강조
    subgraph BiasFilterLayer [Bias Filter Layer]
        E
        F
        G
    end
    style BiasFilterLayer fill:#f9f,stroke:#333,stroke-width:2px,stroke-dasharray: 5 5

    %% 색상 스타일 정의
    classDef core fill:#CCEEFF,stroke:#333
    classDef llm fill:#FFCCAA,stroke:#333
    classDef process fill:#DDFFDD,stroke:#333

    %% 클래스 적용
    class E,G core
    class C llm
    class J process
