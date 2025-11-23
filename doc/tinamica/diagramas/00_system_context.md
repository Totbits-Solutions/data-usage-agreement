graph TD

    %% Personas / Actores
    DC([Data Consumer])
    DP([Data Provider])
    PR([Data Producer])

    %% Sistemas externos
    SD[(Self-Description)]
    BC[(Blockchain)]
    TA[(Trust Anchors /<br/>Compliance)]


    subgraph DUA[DUA Core]
      direction TB
      DUA_API[DUA API]
      DUA_ENGINE[DUA Engine - validación + lifecycle]
    end

    DC -->|Solicita acceso a DataProduct,<br/>acepta y firma DUA| DUA_API
    DP -->|Consulta/crea DUA,<br/>valida acceso| DUA_API
    PR -->|Define condiciones de uso,<br/>firma DUA| DUA_API


    DUA_API --> DUA_ENGINE


    DUA_ENGINE -->|Resuelve @id,<br/>valida participantes| SD
    DUA_ENGINE -->|Registra/consulta DUA,<br/>estado + firmas| BC
    DUA_ENGINE -->|Verifica certificados| TA
