# Modelagem_MER-BD
Modelo Conceitual de Banco de Dados (MER) para o sistema de gerenciamento de ordens de serviço em uma oficina mecânica, desenvolvido como desafio de projeto da DIO.
# Desafio de Projeto: Construindo um Esquema Conceitual para Banco de Dados (Oficina Mecânica)

Repositório criado como parte do desafio de modelagem de dados da formação da **DIO**. O objetivo deste projeto é criar um Modelo Conceitual (MER) do zero para o controle e gerenciamento de ordens de serviço em uma oficina mecânica.

---

## 📋 Descrição do Projeto

O sistema foi desenhado para gerenciar o fluxo completo de atendimento de uma oficina mecânica, cobrindo desde o cadastro de clientes e seus veículos até a emissão de ordens de serviço (OS), alocação de equipes de mecânicos, utilização de peças e cálculo de custos baseados em tabelas de referência de mão de obra.

---

## 🗂️ Estrutura do Modelo Conceitual

O diagrama foi estruturado separando visualmente os blocos operacionais para facilitar a leitura:
* **Bloco Superior (Clientes e Veículos):** Foco no cadastro dos proprietários e dos automóveis atendidos.
* **Bloco Inferior (Execução e Recursos):** Foco nas equipes de trabalho, mecânicos, peças utilizadas, serviços prestados e na emissão das Ordens de Serviço.

### Entidades Principais e Atributos:

1. **Cliente**
   * `id_cliente` (PK)
   * `nome`, `telefone`, `endereco`
2. **Veiculo**
   * `id_veiculo` (PK)
   * `placa`, `modelo`, `marca`, `ano`
   * `id_cliente` (FK)
3. **Equipe**
   * `id_equipe` (PK)
   * `nome_equipe`, `especialidade`
4. **Mecanico**
   * `id_mecanico` (PK)
   * `codigo`, `nome`, `endereco`, `especialidade`
   * `id_equipe` (FK)
5. **Ordem_Servico (OS)**
   * `id_os` (PK)
   * `numero_os`, `data_emissao`, `data_entrega`, `valor_total`, `status`
   * `id_veiculo` (FK), `id_equipe` (FK)
6. **Serviço**
   * `id_serviço` (PK)
   * `descrição`, `valor_mao_de_obra`
7. **Peca**
   * `id_peca` (PK)
   * `descricao`, `valor_unitario`

---

## 🔄 Relacionamentos e Cardinalidade

* **Cliente (1) ── (N) Veículo:** Um cliente pode possuir um ou mais veículos, mas cada veículo pertence a um único cliente.
* **Equipe (1) ── (N) Mecânico:** Uma equipe é composta por vários mecânicos, e cada mecânico pertence a uma única equipe.
* **Veículo (1) ── (N) Ordem de Serviço:** Um veículo possui histórico de várias ordens de serviço ao longo do tempo.
* **Equipe (1) ── (N) Ordem de Serviço:** Uma equipe é responsável por executar várias ordens de serviço.
* **Ordem de Serviço (N) ── (N) Serviço:** Uma OS pode conter múltiplos serviços e um serviço pode estar presente em diversas OS.
* **Ordem de Serviço (N) ── (N) Peça:** Uma OS pode utilizar várias peças e uma mesma peça pode ser aplicada em diferentes ordens de serviço.

---

## 💡 Regras de Negócio Documentadas

1. **Autorização de Execução:** A ordem de serviço possui um campo de `status` (ex: Aberta, Aprovada, Concluída), garantindo que os serviços e peças só são aplicados após a autorização do cliente.
2. **Tabela de Referência:** Os valores cobrados por cada operação consultam uma tabela de referência de mão de obra (`Serviço`) estipulada pela oficina.
3. **Equipe Responsável:** A mesma equipe encarregada de avaliar o veículo e emitir a OS é a responsável por realizar os devidos reparos mecânicos.

---

## 🛠️ Tecnologias Utilizadas
* [Draw.io](https://app.diagrams.net/) (Modelagem Conceitual)
* Git & GitHub (Controle de versão e portfólio)[cite: 1]
