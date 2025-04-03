# README - Configuração de Pesquisa no Microsoft Azure

Este guia explica como configurar um serviço de pesquisa no Azure AI Search, integrado a contêineres de armazenamento (como `coffee-statistic`). Inclui ilustrações do portal Azure e aprendizados práticos.

---

## Passo a Passo Detalhado

### 1. Criar um Serviço de Pesquisa
- **Localização**: `Central US` (ou outra região suportada).
- **Tipo de preço**: `Básico` (ideal para testes).
- **Partições/Réplicas**: 1 (ajuste conforme demanda).

![image](https://github.com/user-attachments/assets/79142abb-da46-4b1b-b76d-9c4c63ba05af)

*(Painel de fundamentos do serviço "avanadeirineu")*

---

### 2. Criar um Índice
- Navegue até **"Índices"** > **"Adicionar índice"**.
- Defina campos como:
  - `Nome` (string, pesquisável)
  - `Descrição` (string, pesquisável)
  - `ID` (chave primária).

![image](https://github.com/user-attachments/assets/9a5434fd-9ace-43e8-b6e3-0e7b5cf6c7f4)


### 3. Importar Dados do Armazenamento
- Use o contêiner **`coffee-statistic`** como fonte:
  - **Tipo de dado**: Blobs JSON/CSV.
  - **Mapeamento**: Associe campos do blob ao índice.

![image](https://github.com/user-attachments/assets/6fbe8152-41c0-4455-ae3a-7d5e5b261f40)

*(Lista de contêineres em `avanadelaboratoriodio`, incluindo `coffee-statistic`)*

---

### 4. Configurar Segurança (IAM)
- Adicione regras no **Controle de Acesso (IAM)**:
  - Restrinja acesso por funções (ex: `Leitor de Dados`).

![image](https://github.com/user-attachments/assets/e03a8839-2c80-4175-82c2-c9a8ad06ea66)

*(Menu de IAM e marcas no serviço)*

---

### 5. Testar no Explorador de Pesquisa
- Execute consultas como:
  ```json
  {
    "search": "café arábica",
    "filter": "preco lt 50"
  }
