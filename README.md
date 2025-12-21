# 📁 Projeto – MVP Engenharia de Dados

## 📄 Visão Geral do Projeto

Este projeto tem como objetivo o desenvolvimento de um **MVP de Engenharia de Dados**, contemplando as etapas de ingestão, processamento, tratamento, governança e modelagem analítica de dados públicos da **Polícia Rodoviária Federal (PRF)**.

O pipeline foi implementado no **Databricks**, seguindo a arquitetura **Lakehouse**, com separação em camadas **RAW**, **BRONZE**, **SILVER** e **GOLD**, garantindo rastreabilidade, qualidade, escalabilidade e reprodutibilidade dos dados.

---

## 📂 Estrutura Geral do Repositório

```text
PUCRIO_MVP_eng_dados/
├── README.md
├── data/
│   ├── acidentes_2007.csv
│   ├── acidentes_2008.csv
|   ├── acidentes_2009.csv
│   ├── acidentes_2010.csv
│   ├── acidentes_2011.csv
│   ├── acidentes_2012.csv
│   └── acidentes_2013.csv
│   ├── acidentes_2014.csv
│   ├── acidentes_2015.csv
│   ├── acidentes_2017.csv
│   ├── acidentes_2018.csv
│   ├── acidentes_2019.csv
│   └── acidentes_2020.csv
|   ├── acidentes_2023.csv
│   ├── acidentes_2024.csv
│   ├── acidentes_2025.csv
├── notebooks/
│   ├── 01_create_catalog.ipynb
│   ├── 02_schema_raw.ipynb
│   ├── 03_schema_bronze.ipynb
│   ├── 04_schema_silver.ipynb
│   └── 05_schema_gold.ipynb
```

---

## 🧱 Notebooks do Pipeline de Dados

### 🗂️ Criação do Catálogo e Schemas  
**Arquivo:** **01_create_catalog.ipynb**

**Objetivo:**  
Configuração inicial do ambiente no Databricks utilizando o **Unity Catalog**.

**Principais ações:**
- Criação do catálogo **lakehouse**
- Criação dos schemas **raw**, **bronze**, **silver** e **gold**
- Criação de **volumes** para armazenamento na camada **RAW**

**Saída:**  
Estrutura de catálogo pronta para ingestão e governança.

---

### 📥 Ingestão de Dados Brutos (RAW)  
**Arquivo:** **02_schema_raw.ipynb**

**Objetivo:**  
Carregar os dados brutos da PRF para a camada **RAW**, preservando o formato original dos arquivos.

**Fontes de dados:**
- Arquivos **CSV/Excel** (anos **2007–2025**)
- Dados públicos da **PRF**

**Técnicas utilizadas:**
- Leitura de múltiplos arquivos
- Upload para **DBFS / Volumes**
- Criação de **tabelas Delta** na camada **RAW**

**Saída:**  
Dados brutos armazenados de forma íntegra na camada **RAW**.

---

### 🧹 Processamento e Limpeza (BRONZE)  
**Arquivo:** **03_schema_bronze.ipynb**

**Objetivo:**  
Padronizar e limpar os dados brutos.

**Transformações aplicadas:**
- Correção de **tipos de dados**
- Padronização de **nomes de colunas**
- Remoção de **duplicidades**
- Tratamento de **valores nulos**
- Conversões seguras para evitar falhas de ingestão

**Saída:**  
Dados consistentes na camada **BRONZE**.

---

### ⚙️ Transformação e Enriquecimento (SILVER)  
**Arquivo:** **04_schema_silver.ipynb**

**Objetivo:**  
Aplicar regras de negócio e enriquecer os dados.

**Ações realizadas:**
- Junção de tabelas
- Criação de colunas derivadas
- Correção de problemas de **encoding**
- Normalização **textual e categórica**
- Aplicação de filtros de **qualidade**

**Saída:**  
Dados tratados e prontos para análise na camada **SILVER**.

---

### 📊 Modelagem Analítica (GOLD)  
**Arquivo:** **05_schema_gold.ipynb**

**Objetivo:**  
Criar métricas, agregações e modelos analíticos para consumo final.

**Entregáveis:**
- Tabelas agregadas (ex.: acidentes por **estado**, **mês** e **tipo**)
- **KPIs** pré-calculados
- **Views** para BI e dashboards
- Modelos de dados **dimensionais**

**Saída:**  
Camada **GOLD** pronta para consumo analítico.

---

## 📈 Fluxo de Dados

```text
Fonte PRF
   ↓
  RAW
   ↓
 BRONZE
   ↓
 SILVER
   ↓
  GOLD
   ↓
Dashboards / BI / Analytics / ML
```

---

## 🔗 Links Úteis

- [Dataset Original (de 2007 a 2020)](https://www.kaggle.com/datasets/equeiroz/acidentes-rodovias-federais-brasil-jan07-a-jul19)
- [Dataset Original (de 2023 a 2025)](https://www.kaggle.com/datasets/jairsouza/acidentes-rodovias-federais)
- [Repo GitHub]( https://github.com/biaacarvalhoo27/PUCRIO_MVP_eng_dados)
- [Dados Abertos da PRF ](https://www.gov.br/prf/pt-br/acesso-a-informacao/dados-abertos/dados-abertos-da-prf)  

---

📅 **Última atualização:** 20/12/2025  
✍️ **Autora:** **Bianca Carvalho Lima**
