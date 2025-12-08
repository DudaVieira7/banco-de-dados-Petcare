# banco-de-dados-Petcare
Cenário do banco de dados:
contexto geral: você é um analista de dados/ analista de sistemas contratado pela clínica PetCare, um clínica veterinária de pequeno porte em expansão.
eles querem substitir o controle atual que é feito em planilhas e cadernos, por um sistema organizado com banco de dados.
Requisitos iniciais (como cliente)
A clínica precisa de um sistema para controlar:
1° animais/pacientes
(a clínica atende: cães, gatos, coelhos e outros animais de pequeno porte)
para cada animal, eles precisam registrar:
* id_animal
* nome
* espécie
* raça
* idade
* sexo
* peso
* data de cadastro
* dono/ responsável (1:N animais)
2° Donos/ tutores
devem conter no cadastro informações como:
* id_dono
* nome completo
* telefone
* email
* endereço
* data de cadastro ( um dono pode ter um ou vários animais: 1:N)
3° Veterinários:
A clínica conta com um time de 4 veterinários fixos.(um veterinário pode atender 1 ou muitos animais : 1:N)
cada veterinário deve ter:
* id veterinário
* nome
* especialidade
* horário de atendimento
* CRMV( número de fiscalização)
* telefone
* email
4° Consultas:
toda consulta deve conter/registrar:
* id_consulta
* id_animal
* id_veterinario
* valor_consulta
* data e hora
* tipo de consulta(avaliação, retorno, vacinação, emrgêngia)
* diagnóstico
* tratamento indicado
* status da consulta (concluida, cancelada, Agendada)
5° Estoque de Medicamentos:
a clínica possui um pequeno estoque e quer aconpanhar:
* id_medicamento
* nome
* categoria
* quantidade_atual
* quantidade_mínima
* data de validade
* fornecedor
* código
se o veteriário prescrever o medicamento deve ser registrado
6° Relatório desajos pelo cliente com o banco de dados:
O cliente pode consultar:
* quantas consultas cada veterinário faz por mês
* animais mais atendidos
* seviços mais realizados
* estoque baixo
* donos que possuem mais de X animais
* faturamento mensal da clínica.
#projeto de modelagem de dados: Clínica Veterinária PetCare 🐾💖

Esse reposotório contentém  a documentação completa usada na criação do banco de dados da PETCARE
##1. Modelagem Conceitual
Nessa etapa, foram definidas as **principais entidades** do sistema e o **relacionamento entre elas**, sem focar em tipos de dados ou chaves primárias, O objetivo foi representar o conhecimento do négocio.
**Principais Entidades.
***Animais.*** Os Pets da Clínica.
***Donos/Tutores.*** próprietários responsáveis pelos animais atendidos.
***Consultas.***  Os agendamentos e servições disponibilizados pela clínica.
***Veterinários.*** Os profíssionais responsavéis pelo atendimento dos Animais atendidos.
***Estoque de Medicamentos***. itens do estoque.

##como é  feito o relacionamento entre as entidades nesse sistema: 
**relacionamentos Chave: **
* DONO (1:N) ANIMAIS: Um Dono pode ter um ou muitos animais.
* ANIMAIS (N: 1) Consultas: Uma Consulta é feita por apenas um animal.
* VETERINARIOS (1:N) Um único veterinário pode fazer várias consultas.

##2. Modelagem Lógica:
A modelagem lógica vem com o objetivo de traduzir o modelo conseitual para uma criação mais abrangente na formação das tabelas iniciais antes de colocar a mão na massa e criar o produto final que é o Modelo físíco. atribuindo **chaves primárias(PK)** e **chaves estrangeiras(FK)** para garantir a integridade dos relacionamentos.
| Tabela | Colunas Chave (PK, FK) | Relacionamentos |
| :--- | :--- | :--- |
| **`animais`** | `id_animal (PK)`, `id_dono (FK)` | `id_dono` referencia `dono(id_dono)` |
| **`dono`** | `id_dono (PK)` | |
| **`consultas`** | `id_consulta (PK)`, `id_animal (FK)`, `veterinario_id (FK)` | Referencia `animais` e `veterinarios` |
| **`veterinarios`** | `veterinario_id (PK)` | |
| **`medicamentos`** | `id_medicamento (PK)` | |



---

## 3. Modelagem Física
Esta etapa define o esquema do banco de dados (DDL - Data Definition Language) com tipos de dados, tamanhos e restrições específicas para o SGBD (Sistema Gerenciador de Banco de Dados) utilizado (Ex: PostgreSQL, MySQL).

> **O script completo de criação das tabelas pode ser encontrado em:** `sql/01_criação_tabelas.sql`

**Exemplo de Definição (Tabela `animais`):**
```sql
CREATE TABLE animais (
    id_animal SERIAL PRIMARY KEY,
    nome_animal VARCHAR(100) NOT NULL,
    especie_animal VARCHAR(50),
    raca_animal VARCHAR(100),
    sexo_animal CHAR(1),
    peso_animal NUMERIC(5, 2),
    datanasc_animal DATE,
    id_dono INT REFERENCES dono(id_dono)
);


##4. Dados
Todos os dados utilizados para popular o banco e testar as operações CRUD e relatórios. estão desponbilizados nesse repositório com todas as  funções usadas na criação  e algumas utilizadas execução
 procedimentos para teste;



  
