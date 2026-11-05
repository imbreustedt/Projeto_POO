# 📅 Sistema de Agendamento e Gestão de Atendimentos

Um sistema web completo para gerenciamento de consultas, serviços e atendimentos clínicos/estéticos, desenvolvido em **Python** utilizando **Streamlit** e arquitetura em camadas (**Model - DAO - Service - UI**).

[![GitHub repo](https://img.shields.io/badge/GitHub-Projeto__POO-blue?style=flat&logo=github)](https://github.com/imbreustedt/Projeto_POO)

---

## 📌 Sumário
- [Sobre o Projeto](#-sobre-o-projeto)
- [Funcionalidades por Perfil](#-funcionalidades-por-perfil)
- [Arquitetura do Sistema](#-arquitetura-do-sistema)
- [Tecnologias Utilizadas](#-tecnologias-utilizadas)
- [Como Executar o Projeto](#-como-executar-o-projeto)
- [Estrutura de Arquivos](#-estrutura-de-arquivos)
- [Acesso Padrão](#-acesso-padrão-administrador)

---

## 🚀 Sobre o Projeto

O **Projeto POO** é uma aplicação web desenvolvida para automatizar a gestão de agendas e atendimentos em clínicas ou empresas prestadoras de serviço. Ele permite que profissionais de saúde/atendimento disponibilizem seus horários, clientes façam agendamentos e acompanhem seus serviços, e administradores tenham controle total sobre os cadastros do sistema.

---

## 🔑 Funcionalidades por Perfil

### 🌐 Visitante (Não Autenticado)
- **Entrar no Sistema**: Autenticação unificada para clientes e profissionais.
- **Abrir Conta**: Cadastro rápido de novos clientes.

### 👤 Cliente
- **Meus Dados**: Visualização e atualização das informações de perfil e senha.
- **Agendar Serviço**: Seleção de profissional, horário disponível e tipo de serviço.
- **Meus Serviços**: Acompanhamento dos horários marcados e status de confirmação.
- **Pagar Atendimento**: Visualização e pagamento de atendimentos concluídos.

### 🩺 Profissional
- **Meus Dados**: Atualização dos dados de perfil e especialidade.
- **Abrir Agenda**: Geração automática de grade de horários configurando data, horário inicial, horário final e intervalo (em minutos).
- **Minha Agenda**: Visualização da agenda completa do profissional.
- **Confirmar Serviço**: Aprovação das solicitações de agendamento feitas pelos clientes.
- **Registrar Atendimento**: Inserção de prontuário (queixa principal, histórico de saúde, avaliação clínica e prescrição) e vínculo dos serviços realizados com cálculo automático do valor final.

### 👑 Administrador (`admin`)
- **Gestão de Clientes (CRUD)**: Listar, cadastrar, editar e remover clientes.
- **Gestão de Profissionais (CRUD)**: Listar, cadastrar, editar e remover profissionais e especialidades.
- **Gestão de Serviços (CRUD)**: Gerenciar catálogo de serviços e valores.
- **Gestão de Horários (CRUD)**: Controle global da grade de horários.
- **Gestão de Atendimentos (CRUD)**: Controle centralizado de atendimentos registrados.
- **Alterar Senha**: Atualização da senha de acesso do administrador.

---

## 🏗️ Arquitetura do Sistema

O projeto adota uma arquitetura orientada a objetos modularizada:

1. **`Models`**: Define as entidades do domínio (`Cliente`, `Profissional`, `Servico`, `Horario`, `Atendimento`, `AtendimentoItem`) com encapsulamento e validações.
2. **`DAOs` (Data Access Objects)**: Responsáveis por ler e gravar os dados serializados em formato JSON na pasta `jsons/`.
3. **`Service`**: Camada que centraliza as regras de negócio, lógica de agendamento, autenticação e cálculos.
4. **`Templates` (UI)**: Módulos de interface gráfica desenvolvidos com Streamlit.
5. **`IndexUI` (`index.py`)**: Controlador principal da aplicação e navegação entre menus por perfil de usuário.

---

## 🛠️ Tecnologias Utilizadas

- **[Python 3.x](https://www.python.org/)**
- **[Streamlit](https://streamlit.io/)** - Interface de usuário web
- **[Pandas](https://pandas.pydata.org/)** - Exibição de dados tabulares
- **JSON** - Persistência leve de dados em arquivos

---

## 💻 Como Executar o Projeto

### Pré-requisitos
- Python 3.8 ou superior instalado.
- Git instalado.

### Passo a Passo

1. **Clonar o repositório:**
   ```bash
   git clone https://github.com/imbreustedt/Projeto_POO.git
   cd Projeto_POO
   ```

2. **Criar e ativar um ambiente virtual (recomendado):**
   ```bash
   # Linux / macOS
   python3 -m venv venv
   source venv/bin/activate

   # Windows (PowerShell)
   python -m venv venv
   .\venv\Scripts\Activate.ps1
   ```

3. **Instalar as dependências:**
   ```bash
   pip install streamlit pandas
   ```

4. **Executar a aplicação:**
   ```bash
   streamlit run index.py
   ```

5. **Acessar a interface:**
   Abra seu navegador no endereço: `http://localhost:8501`.

---

## 📁 Estrutura de Arquivos

```text
.
├── index.py                    # Ponto de entrada da aplicação Streamlit
├── service.py                  # Camada de Regras de Negócio (Service)
├── models/                     # Entidades e Classes DAO para persistência
│   ├── atendimento.py
│   ├── atendimentodao.py
│   ├── atendimentoitem.py
│   ├── atendimentoitemdao.py
│   ├── cliente.py
│   ├── clientedao.py
│   ├── horario.py
│   ├── horariodao.py
│   ├── profissional.py
│   ├── profissionaldao.py
│   ├── servico.py
│   └── servicodao.py
├── templates/                  # Componentes de Interface Gráfica (Streamlit)
│   ├── abriragendaui.py
│   ├── abrircontaui.py
│   ├── agendarservicoui.py
│   ├── alterarsenhaui.py
│   ├── confirmarservicoui.py
│   ├── loginui.py
│   ├── manteratendimentoui.py
│   ├── manterclienteui.py
│   ├── manterhorarioui.py
│   ├── manterprofissionalui.py
│   ├── manterservicoui.py
│   ├── pagaratendimentoui.py
│   ├── perfilclienteui.py
│   ├── perfilprofissionalui.py
│   ├── registraratendimentoui.py
│   ├── visualizaragendaui.py
│   └── visualizarservicosui.py
└── jsons/                      # Arquivos JSON de persistência de dados
```

---

## 🔑 Acesso Padrão (Administrador)

Ao executar o sistema pela primeira vez, a conta do Administrador é criada automaticamente:

- **E-mail / Usuário:** `admin`
- **Senha:** `1234`

---

## 👤 Autor

Desenvolvido por **[imbreustedt](https://github.com/imbreustedt)** durante o curso de INFOWEB/2026.
