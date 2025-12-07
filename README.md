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
  
