sequenceDiagram
autonumber
participant DC as DataConsumer
participant DP as DataProvider
participant BC as Blockchain/DUA Registry

    DC->>DP: 1. Solicita acceso a DataProduct
    DP->>DP: 2. Verifica internamente si existe DUA válido


    DP->>DP: 3. Solicita creación/aceptación de un nuevo DUA

    DP->>DP: 4. Construye borrador de DUA (JSON-LD + ontología Gaia-X)
    DP->>DP: 5. Realiza validaciones internas / notarización lógica

    DP->>BC: 6. Registra DUA en estado "PENDING_SIGNATURES"
    BC-->>DP: 7. Confirmación de registro

    DP-->>DC: 8. Notifica que hay un DUA pendiente de firmas
