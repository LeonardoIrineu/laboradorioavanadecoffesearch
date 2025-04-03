# README - Configuração de Pesquisa no Microsoft Azure

Este guia explica como configurar um serviço de pesquisa no Azure AI Search, integrado a contêineres de armazenamento (como `coffee-statistic`). Inclui ilustrações do portal Azure e aprendizados práticos.

---

## Passo a Passo Detalhado

### 1. Criar um Serviço de Pesquisa
- **Localização**: `Central US` (ou outra região suportada).
- **Tipo de preço**: `Básico` (ideal para testes).
- **Partições/Réplicas**: 1 (ajuste conforme demanda).

![Configuração do Serviço](image.png)  
*(Painel de fundamentos do serviço "avanadeirineu")*

---

### 2. Criar um Índice
- Navegue até **"Índices"** > **"Adicionar índice"**.
- Defina campos como:
  - `Nome` (string, pesquisável)
  - `Descrição` (string, pesquisável)
  - `ID` (chave primária).

![image](image.png)  
*(Resultado vazio ao consultar `coffee-index` antes da importação de dados)*

---

### 3. Importar Dados do Armazenamento
- Use o contêiner **`coffee-statistic`** como fonte:
  - **Tipo de dado**: Blobs JSON/CSV.
  - **Mapeamento**: Associe campos do blob ao índice.

![Contêineres de Armazenamento](image.png)  
*(Lista de contêineres em `avanadelaboratoriodio`, incluindo `coffee-statistic`)*

---

### 4. Configurar Segurança (IAM)
- Adicione regras no **Controle de Acesso (IAM)**:
  - Restrinja acesso por funções (ex: `Leitor de Dados`).

![Controle de Acesso]()  
*(Menu de IAM e marcas no serviço)*

---

### 5. Testar no Explorador de Pesquisa
- Execute consultas como:
  ```json
  {
    "search": "café arábica",
    "filter": "preco lt 50"
  }
