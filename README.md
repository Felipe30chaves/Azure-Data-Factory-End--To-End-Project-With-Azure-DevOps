# Azure-Data-Factory-End--To-End-Project-With-Azure-DevOps

### Azure Data Factory — Medallion Data Platform (E2E)

Plataforma de dados end-to-end na Azure usando Arquitetura Medallion (Bronze/Silver/Gold), Azure Data Factory para orquestração, Databricks/PySpark para transformação e Azure SQL DB para serving. Inclui pipelines dinâmicos, cargas incrementais e integração com GitHub/Azure DevOps.

### 🧱 Stack

Ingestão: Azure Data Factory (Copy Activity: On-Prem/Files/API → ADLS Gen2)

Transformação: Databricks PySpark (limpeza, padronização, upsert)

Armazenamento: Data Lake Gen2 (Bronze/Silver/Gold)

Serviço Analítico: Azure SQL DB (tabelas de consumo e views de negócio)

Orquestração: ADF Pipelines (parâmetros, dynamic mapping, dependências, triggers)

Observabilidade: ADF Monitor + Logic Apps (alertas)

Controle de Acesso/Segredos: (opcional) Azure Key Vault

CI/CD: GitHub (feature branch + PR) e/ou Azure DevOps

### ✨ Funcionalidades

Arquitetura Medallion:

Bronze: raw imutável (arquivos/JSON/CSV).

Silver: curado e normalizado (PySpark).

Gold: business views e agregações.

Cargas Incrementais: watermark por coluna de data/offset + merge/upsert idempotente.

Pipelines Dinâmicos: parametrização de fonte/destino/esquema e schema drift via mapping dinâmico.


.
├─ adf/
│  ├─ linkedServices/
│  ├─ datasets/
│  ├─ pipelines/
│  └─ globalParameters.json
├─ databricks/
│  ├─ bronze/
│  ├─ silver/
│  └─ gold/
├─ sql/
│  ├─ ddl/
│  └─ views/
├─ docs/
│  └─ arquitetura.png   <-- coloque a imagem aqui
└─ README.md


APIs: extração via ADF HTTP + desserialização/normalização.

On-Prem → Cloud: self-hosted integration runtime (quando necessário).

Dev → Prod: branches, PRs e Releases (exemplos de YAML opcional).
