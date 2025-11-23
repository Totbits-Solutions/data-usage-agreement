# ¿Qué es un Trust Anchor en GAIA-X?

Un **Trust Anchor** es una **entidad reconocida y validada por GAIA-X** cuya función es **emitir, verificar y respaldar información confiable** dentro del ecosistema GAIA-X.

Es decir:

> **Un Trust Anchor es una autoridad de confianza que respalda la veracidad de la información declarada por un participante en GAIA-X.**

GAIA-X adopta el modelo de **Verifiable Credentials (VC)** basado en “Issuer / Holder / Verifier”, y dentro de ese modelo, el **Issuer** es el **Trust Anchor**.

## ¿Cuál es su rol dentro de GAIA-X?

Un **Trust Anchor** sirve para:

### Verificar información proporcionada por participantes

(empresa, proveedor, data provider, data producer, etc.)

### Emitir Verifiable Credentials (VC) firmadas

que certifican que ciertos atributos son válidos.

### Garantizar la integridad y autenticidad de los datos

ej. número de registro mercantil, VAT ID, EORI, LEI, etc.

### Servir como raíz de confianza (similar a un CA en SSL)

Toda clave que firma Self-Descriptions debe tener en su **cadena de certificados** al menos un Trust Anchor reconocido.

## Referencia exacta GAIA-X

> “Trust Anchors are entities endorsed by Gaia-X. Trust Anchors shall underpin claims by Participants… They will affirm the necessary trust in otherwise mere self-declared statements.”
> **(GAIA-X Trust Framework, sección Trust Anchors)**

## ¿Qué comprueba GAIA-X respecto a los Trust Anchors?

Cuando el **Gaia-X Compliance Service** verifica unos datos:

1. Que las declaraciones siguen el formato correcto
2. Que el emisor (Issuer) está registrado en el **Gaia-X Registry**
3. Que esa información es consistente
4. Que la clave de firma del participante está asociada a un **Trust Anchor**

## Referencia

> “To be compliant… keypairs used to sign claims must have at least one of the Trust Anchors in their certificate chain.”

## Tipos de Trust Anchors reconocidos por GAIA-X

### **1. State (TSP estatales)**

- Autoridades eIDAS de firma electrónica cualificada (QTSP)
- Certificados EV SSL como mecanismo temporal

### **2. eiDAS**

Emisores europeos de certificados cualificados

### **3. EV SSL**

Aceptados temporalmente como Trust Service Providers (TSP)

### **4. registrationNumberIssuer**

En la fase piloto, **GAIA-X Association** actúa como Trust Anchor en:
[https://notary.gaia-x.eu](https://notary.gaia-x.eu)

## ¿Cómo funciona un Trust Anchor en la práctica?

### Caso 1 — Si una entidad reclama un atributo

por ejemplo:

- Su VAT ID
- Su LEI
- Su Local Registration Number

El Trust Anchor:

1. Consulta el **Trusted Data Source** correspondiente
2. Comprueba la autenticidad
3. Firma un **Verifiable Credential (VC)**
4. Devuelve el VC al participante
5. El participante lo almacena en su wallet
6. Ese VC es usado como **prueba verificable** en GAIA-X

## Caso 2 — Durante la verificación GAIA-X

Cuando un participante necesita demostrar que su información es legítima:

1. Selecciona un VC en su wallet
2. Lo presenta al GAIA-X Compliance Service
3. El servicio comprueba:

   - Si el VC está firmado por un Trust Anchor
   - Si el Trust Anchor está en el GAIA-X Registry
   - Si el contenido del VC coincide con la Self-Description

Si todo es correcto, GAIA-X emite un:

→ **Gaia-X Compliance VC**

## Referencia

Sección “4.5 Compliance verification”

# ¿Cómo se relaciona esto con un DUA?

En un **Data Usage Agreement**, la propiedad:

```
gx:dataUsageAgreementTrustAnchor
```

Es:

→ Un enlace a un documento o entidad que actúa como **fundamento de confianza**
(contrato maestro, política, o certificación vinculada a un Trust Anchor).

Por ejemplo:

```
"gx:dataUsageAgreementTrustAnchor": "https://docs.gaia-x.eu/policy-rules-committee/compliance-document/24.11/Gaia-X_Trust_Anchors/"
```

O una política legal firmada y publicada por un Trust Anchor.

# Resumen rápido — Trust Anchor en GAIA-X

| Concepto         | Explicación                                               |
| ---------------- | --------------------------------------------------------- |
| Qué es           | Una autoridad de confianza que respalda información       |
| Función          | Emitir/verificar Verifiable Credentials                   |
| Relación con DUA | Actúa como “base legal / raíz de confianza” para acuerdos |
| Registro         | Debe estar en el GAIA-X Registry                          |
| Certificados     | Toda firma debe encadenar a un Trust Anchor               |
| Ejemplos         | eIDAS, EV SSL, Gaia-X Notary                              |
