sequenceDiagram
autonumber
participant DC as DataConsumer
participant DP as DataProvider
participant BC as Blockchain/DUA Registry

    DC->>DP: 1. Solicita acceso / reuso del DataProduct

    DP->>BC: 2. Consulta DUA válido
    BC-->>DP: 3. Devuelve DUA + estado

    alt DUA válido y activo
        DP->>DP: 4. Verificación interna
        DP-->>DC: 5.1. Entrega acceso a los datos
    else DUA expirado o revocado
        DP-->>DC: 5.2. Deniega acceso y propone nuevo DUA
    end
