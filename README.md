# Bot de Gerenciamento Casa das Debutantes

Este é um Bot de gerenciamento local, desenvolvido em Python com interface gráfica Tkinter e banco de dados SQLite, para auxiliar a empresa "Casa das Debutantes" no controle de clientes, estoque de roupas, fluxo de caixa e comunicação via WhatsApp Business API.

## 1. Pré-requisitos

Para rodar o Bot, você precisará ter instalado:

*   **Python 3.x** (O projeto foi desenvolvido com foco na compatibilidade com Python 3.14, mas deve funcionar em versões 3.8+).
*   **Tkinter** (Geralmente já vem instalado com o Python padrão).
*   **Biblioteca `requests`** (Para comunicação com a API do WhatsApp).

## 2. Configuração e Instalação

1.  **Navegue até a pasta do projeto:**
    ```bash
    cd casa_das_debutantes_bot
    ```

2.  **Instale as dependências necessárias:**
    ```bash
    pip install requests
    ```

3.  **Estrutura de Arquivos:**
    O projeto é composto por três arquivos principais:
    *   `main_app.py`: O arquivo principal que contém a interface gráfica (Tkinter) e a lógica de interação.
    *   `database.py`: O módulo responsável por gerenciar a conexão com o banco de dados SQLite (`bot_data.db`) e a criação das tabelas.
    *   `whatsapp_api.py`: O módulo que encapsula a lógica de comunicação com a API do WhatsApp Business.

## 3. Como Executar

Execute o arquivo principal a partir do terminal:

```bash
python main_app.py
```

O banco de dados (`bot_data.db`) será criado automaticamente na primeira execução.

## 4. Funcionalidades do Bot

O Bot é dividido em quatro abas principais:

### 4.1. Clientes

Permite o cadastro e a pesquisa de clientes.

| Campo | Descrição | Obrigatório |
| :--- | :--- | :--- |
| Nome | Nome completo do cliente. | Sim |
| Data de Nascimento | Data de nascimento. | Não |
| CPF | Cadastro de Pessoa Física (deve ser único). | Sim |
| Sexo | Sexo do cliente. | Não |
| Última Roupa Alugada | Informação sobre o último item alugado. | Não |

A pesquisa pode ser feita por **Nome** (busca parcial) ou **CPF** (busca exata).

### 4.2. Roupas

Permite o cadastro, visualização e edição do estoque de roupas.

| Campo | Descrição |
| :--- | :--- |
| Nome | Nome da roupa (ex: Vestido de Festa Azul). |
| Modelo | Modelo específico da roupa. |
| Tamanho | Tamanho (ex: P, M, G). |
| Numeração | Numeração específica (se aplicável). |
| Último a Alugar | Nome do último cliente que alugou a peça. |
| Disponibilidade | **Disponível** ou **Alugado** (campo obrigatório). |
| Histórico de Aluguel | O sistema registra automaticamente o histórico de aluguel. |

**Edição:** Dê um **clique duplo** em qualquer item da lista para carregar os dados nos campos de edição.

### 4.3. Fluxo de Caixa

Gerencia as finanças da empresa com controle de entradas, saídas, contas a pagar e a receber.

*   **Registro de Transação:** Permite registrar o **Tipo** (Entrada, Saída, A Pagar, A Receber), **Valor**, **Data** e **Descrição**.
*   **Status:** Transações do tipo *Entrada* e *Saída* são marcadas como **Concluídas** (pago/recebido) automaticamente. Transações *A Pagar* e *A Receber* são marcadas como **Pendentes**.
*   **Marcar como Pago/Recebido:** Selecione uma transação pendente na lista e clique no botão para mudar seu status para **Concluído**.
*   **Resumo Financeiro:** Calcula e exibe o **Total de Entradas**, **Total de Saídas**, **Contas a Receber**, **Contas a Pagar** e o **Lucro Líquido** (Entradas - Saídas).

### 4.4. WhatsApp

Esta aba é crucial para a comunicação e requer configuração externa.

#### 4.4.1. Configuração da API

Para que o Bot possa enviar mensagens, você deve obter as seguintes informações da plataforma **Meta for Developers** (Facebook/Meta):

1.  **Token da API do WhatsApp:** Um token de acesso gerado pela Meta.
2.  **ID do Telefone (Phone ID):** O ID do número de telefone que você registrou no WhatsApp Business API.

**Atenção:** O Bot funciona localmente e simula o envio de mensagens através da API da Meta. Para **receber** mensagens e ter o recurso de resposta programada totalmente funcional, você precisaria de um servidor público para configurar um **Webhook**, o que está fora do escopo desta aplicação local.

#### 4.4.2. Funcionalidades de Comunicação

*   **Enviar Mensagem/Arquivo:** Permite enviar mensagens de texto ou arquivos (via URL pública) para qualquer número de WhatsApp, utilizando as credenciais salvas.
*   **Testar Resposta Programada:** Simula o recebimento de uma mensagem e exibe a resposta automática que o Bot geraria com base na lógica pré-definida (ex: se a mensagem contiver "olá", ele responde com uma saudação e opções).

## 5. Código-Fonte

O código-fonte está dividido nos arquivos `main_app.py`, `database.py` e `whatsapp_api.py`.

---
*Desenvolvido por Manus AI*
