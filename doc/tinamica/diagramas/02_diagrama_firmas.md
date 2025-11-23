sequenceDiagram
autonumber
participant DC as DataConsumer
participant DP as DataProvider
participant PR as DataProducer
participant BC as Blockchain/DUA Registry

    note over DC,DP: Cada parte accede al DUA y realiza su firma.

    DC->>DP: 1. Solicita firmar DUA
    DP-->>DC: 2. Obtiene DUA (PENDING_SIGNATURES)
    DP->>DC: 3. Devuelve DUA para firmar

    DC->>DP: 4. Envía firma (on-chain o prueba off-chain)
    DP->>BC: 5. Registra firma de DC
    BC-->>DP: 6. Confirmación

    DP->>DP: 7. Provider firma el DUA
    DP->>BC: 8. Registra firma del Provider
    BC-->>DP: 9. Confirmación

    PR->>DP: 10. Producer firma el DUA
    DP->>BC: 11. Registra firma del Producer
    BC-->>DP: 12. Confirmación

    DP->>DP: 13. Valida internamente que se han cumplido todos los "gx:signers"
    DP->>DP: 14. Ejecuta notarización interna (rol DUA Notary integrado)

    DP->>BC: 15. Actualiza DUA a estado "ACTIVE"
    BC-->>DP: 16. Confirmación

    DP-->>DC: 17. DUA activo — el DataProduct ya puede ser consumido
