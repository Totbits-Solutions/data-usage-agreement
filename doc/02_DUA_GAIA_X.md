# 1. ¿Qué es un DUA (Data Usage Agreement) en GAIA-X?

Un **Data Usage Agreement (DUA)** es un documento semántico en formato **JSON-LD** que describe un **acuerdo de uso de datos entre participantes** dentro del ecosistema GAIA-X.

Define:

- Quién produce los datos (_Data Producer_)
- Quién los provee o los distribuye (_Data Provider_)
- Qué data product se usa (_Data Product_)
- Bajo qué condiciones legales y contractuales se puede usar (_Terms, Licenses_)
- Qué partes deben firmar para que el acuerdo sea válido (_Signers_)

Es parte del modelo oficial de datos de GAIA-X, **clase `gx:DataUsageAgreement`**.

### Referencia oficial GAIA-X

- _GAIA-X Ontology_: `gx:DataUsageAgreement`
  [https://w3id.org/gaia-x/development#data-exchange-wg](https://w3id.org/gaia-x/development#data-exchange-wg)

# 2. ¿Qué propiedades tiene un DUA?

Según la ontología oficial, un DUA tiene las siguientes propiedades clave:

### **Propiedades obligatorias**

- **`gx:producedBy`** → enlace resoluble al _Data Producer_
- **`gx:providedBy`** → enlace al _Data Provider_
- **`gx:dataProduct`** → enlace al _Data Product_ al que aplica el DUA
- **`gx:dataUsageAgreementTrustAnchor`** → enlace a un "trust anchor" (documento o política superior)
- **`gx:signers`** → lista de participantes que deben firmar
  (instancias de `gx:SignatureCheckType`)

### **Propiedades opcionales**

- **`gx:licensedBy`** → licenciante de los datos
- **Cualquier metadato legal adicional** que quieras enlazar desde Self-Descriptions

Estos atributos provienen de la sección:

### Referencia oficial GAIA-X

- _Data Exchange WG — Data Usage Agreement_
  [https://w3id.org/gaia-x/development#data-exchange-wg](https://w3id.org/gaia-x/development#data-exchange-wg)
- _Ontology SHACL shapes_: restricciones sobre roles y cardinalidad

# 3. ¿Para qué sirve crear un DUA?

En GAIA-X sirve para **formalizar, describir y verificar** las condiciones bajo las cuales un usuario o empresa puede **usar un dataset o data product**.

Un DUA permite:

### **Transparencia**

Describe quién hace qué con los datos y bajo qué términos.

### **Interoperabilidad**

Cualquier nodo GAIA-X, data exchange o servicio puede leer el acuerdo gracias al estándar JSON-LD + ontología GAIA-X.

### **Automatización**

Permite a servicios automatizados validar el uso permitido antes de permitir acceso a los datos.

### **Confianza**

Puede enlazarse a un **trust anchor** (política superior, contrato legal, certificación), permitiendo trazabilidad.

### **Verificación on-chain (opcional)**

Puedes anclar el hash de un DUA en blockchain para garantizar que no se ha modificado.

### Referencia oficial GAIA-X

- _Self-Description Framework_:
  Los acuerdos y descripciones se usan para establecer confianza verificable.
  [https://w3id.org/gaia-x/development](https://w3id.org/gaia-x/development)

# 4. ¿Cómo se construye un DUA? (en teoría)

Construir un DUA sigue este proceso conceptual:

### **1. Identificación de las partes**

Determinar:

- Data Producer
- Data Provider
- Data Product
- Licenciantes (si aplica)
- Participantes obligados a firmar

Todos deben tener Self-Descriptions válidas (JSON-LD GAIA-X).

### **2. Establecer el contexto semántico**

Todo DUA debe incluir:

```
"@context": [
  "https://w3id.org/gaia-x/development",
  { … prefijos usados … }
]
```

### **3. Enlazar las entidades**

El DUA no contiene la información completa; **apunta** a otros JSON-LD:

- `gx:producedBy`: URL del DataProducer.jsonld
- `gx:providedBy`: URL del DataProvider.jsonld
- `gx:dataProduct`: URL de DataProduct.jsonld

### **4. Definir el trust anchor**

Documento o política principal que rige el contrato:

```
"gx:dataUsageAgreementTrustAnchor": "https://example.com/trust-anchor"
```

### **5. Declarar los firmantes**

Cada firmante se describe como `gx:SignatureCheckType`.

### Referencias oficiales GAIA-X

- _Ontology_ — propiedades de DataUsageAgreement
- _Data Exchange WG_ — modelo de intercambio de datos
- _Self Description Lifecycle_ — creación y verificación de descripciones

# 5. ¿Cómo se interactúa con un DUA?

Hay tres modos principales:

## **A. Interacción Off-Chain (estándar GAIA-X)**

Cualquier servicio puede:

1. Descargar el JSON-LD
2. Expandirlo con JSON-LD 1.1
3. Validarlo con SHACL usando las shapes oficiales
4. Comprobar roles, signers y restricciones del DUA

## **B. Integración en consumidores de datos**

Un Data Provider puede:

- Leer el DUA del Data Product
- Verificar si el consumidor tiene permisos
- Aplicar políticas basadas en `gx:signers`, licencias, etc.

### Referencia oficial GAIA-X

- _Self-Descriptions — Verification_
- _Trust Framework_
- _Policy Enforcement_
  [https://w3id.org/gaia-x/development](https://w3id.org/gaia-x/development)
