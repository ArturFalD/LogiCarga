#  LogiCarga - Sistema Otimizador de Entregas Logísticas e Previsão de Demanda

> **Projeto Prático Integrador (PPI)**  
> **Instituição:** Instituto Federal Farroupilha (IFFar) — Campus Frederico Westphalen  
> **Cliente/Contexto:** Central de Logística da Cotrifred  

---

## Sobre o Projeto

O **LogiCarga** é uma solução de software desenvolvida para otimizar os processos da central de logística da cooperativa Cotrifred, abrangendo desde o registro de vendas até a entrega final ao cliente.

Anteriormente executado de forma manual e fragmentado através de múltiplos aplicativos, o processo logístico foi centralizado em uma única plataforma web e mobile. O sistema oferece automação de cadastro de vendas, planejamento e organização de carga em caminhões, confirmação digital de entrega via canhoto de nota fiscal e **previsão inteligente de recompra por Inteligência Artificial**.

---

## Objetivos Principais

- **Redução da Redundância:** Eliminar duplicidade em pedidos e inconsistências de dados.
- **Eficiência Operacional:** Otimizar o tempo de gerenciamento logístico e montagem de cargas.
- **Rastreabilidade:** Garantir confirmação em tempo real das entregas sem depender de apps externos.
- **Inteligência de Vendas:** Prever a demanda futura dos clientes e sugerir momentos ideais de recompra.

---

##  Principais Funcionalidades

O sistema possui controle de acesso granular baseado nas funções dos usuários (**Role-Based Access Control - RBAC**):

###  1. Administrador
- CRUD completo de usuários e gerenciamento de perfis/permissões (Administrador, Logística, Vendedor, Motorista).
- Edição e exclusão avançada de cadastros gerais.

###  2. Vendedores
- **Gestão de Clientes & Vendas:** Cadastro, edição e consulta de clientes e pedidos de venda.
- **Lembretes Automatizados:** Criação de lembretes manuais e notificações baseadas em sugestões do sistema.
- **Acompanhamento:** Visualização do status de processamento e entrega dos pedidos.

###  3. Equipe de Logística
- **Gestão de Cargas & Entregas:** Consolidação de múltiplos pedidos pendentes em ordens de entrega.
- **Sugestão de Organização do Caminhão:** Algoritmo que sugere a disposição mais eficiente das caixas e pesos no veículo.
- **Painel de Acompanhamento:** Monitoramento das entregas em andamento e relatórios de desempenho.

###  4. Motoristas
- **Aplicativo/Interface Mobile:** Acesso à rota de entregas designadas.
- **Confirmação Digital:** Envio de confirmação de entrega com registro de recebedor e foto da nota fiscal/canhoto.
- **Registro de Ocorrências:** Marcação de devoluções ou falhas na entrega com justificativas padronizadas.

---

##  Módulo de Inteligência Artificial (Previsão de Demanda)

Para auxiliar os vendedores na antecipação de compras e retenção de clientes, o **LogiCarga** conta com um modelo preditivo baseado em Machine Learning.

- **Objetivo:** Estimar o número de dias até a próxima compra do cliente.
- **Variáveis Consideradas:**
  - Histórico de dias entre compras por cliente.
  - Sazonalidade (mês da compra).
  - Volume e tipo de ração adquirida.
  - Comportamento acumulado do comprador.
- **Metodologia de Validação:** Treinamento com histórico pré-2026 e teste/validação com dados do período atual (2026+).

---

##  Arquitetura do Sistema

### Stack Tecnológica
- **Backend:** Go (Golang) — Alta performance, simplicidade e concorrência nativa.
- **Frontend:** React + Vite + Tailwind CSS — Interface moderna, responsiva e otimizada para desktop e dispositivos móveis.
- **Banco de Dados:** PostgreSQL — Consistência, integridade referencial e escalabilidade.
- **Machine Learning:** Python (Scikit-Learn, Pandas) — Treinamento e inferência do modelo preditivo.

---

##  Modelo do Banco de Dados

O banco de dados relacional foi modelado para garantir integridade e rastreabilidade:

### Principais Tabelas:
- `Usuario`: Armazena dados de acesso, CPF, função e credenciais.
- `Cliente` & `Logradouro`: Endereçamento e dados dos compradores com suporte a coordenadas geográficas (latitude/longitude).
- `Veiculo`: Frota com capacidade máxima de peso e placa.
- `Item`: Produtos/Rações comercializados.
- `Venda` & `Venda_Item`: Pedidos realizados, vinculados ao cliente e vendedor.
- `Entrega`: Agrupamento de vendas atribuídas a um motorista e veículo.
- `Lembrete`: Sistema de alertas para vendedores.

---