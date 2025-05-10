O cenário escolhido foi o de uma clínica médica com múltiplas especialidades, que envolve a gestão de:

Pacientes (cadastro, histórico médico, alergias, convênios)
Médicos (especialidades, CRM, contato, salários)
Agendamentos (marcação de consultas, status)
Consultas (diagnósticos, observações)
Receitas (medicamentos prescritos, posologia)
Pagamentos (formas de pagamento, status financeiro)

É um sistema realista e comum, presente em diversas instituições de saúde, 
Possui relacionamentos complexos (médico-especialidade, paciente-consulta, receita-medicamento), o que permite explorar bem os conceitos de chaves primárias e estrangeiras.

Permite consultas interessantes, como:
Quantidade de consultas por médico.
Medicamentos mais prescritos.
Faturamento por especialidade.

Estrutura do Projeto (DDL - Data Definition Language)
Tabelas Principais
Especialidades

Armazena as áreas médicas (Cardiologia, Dermatologia, etc.).
Relacionada com a tabela Medicos.

Medicos
Cadastro dos médicos, com CRM (único), salário e especialidade.
Possui uma flag ativo para controle de demissões.

Pacientes
Dados pessoais, alergias e convênio.
CPF como campo único para evitar duplicações.

Agendamentos
Registra as marcações de consultas, com status (agendado, realizado, cancelado, faltou).
Relaciona Pacientes e Medicos.

Consultas
Detalhes das consultas realizadas (diagnóstico, horários).
Só existe se o agendamento foi marcado como realizado.

Receitas
Prescrições médicas, com validade e instruções.
Relacionada com Consultas.

Medicamentos
Catálogo de remédios (nome, fabricante, princípio ativo).

ItensReceita
Itens específicos de cada receita (posologia, quantidade).
Relaciona Receitas e Medicamentos.

Pagamentos
Registro financeiro das consultas (valor, forma de pagamento, status).
Relacionado com Consultas.

Operações Realizadas (DML - Data Manipulation Language)
1. Inserção de Dados (INSERT)
Cada tabela foi populada com pelo menos 10 registros, garantindo dados realistas:
10 especialidades médicas (Cardiologia, Dermatologia, etc.).
10 médicos, cada um com uma especialidade.
10 pacientes, com informações completas.
10 agendamentos, com diferentes status.
8 consultas (apenas para agendamentos realizados).
7 receitas (nem toda consulta gera receita).
10 medicamentos no catálogo.
7 itens de receita (ligando receitas a medicamentos).
8 pagamentos (um para cada consulta realizada).

2. Atualizações (UPDATE)
Ajuste de salário de um médico (aumento de 10%).
Atualização de status de pagamento (de pendente para pago).
Alteração de telefone de um paciente.
Marcação de médico como inativo (simulando uma demissão).
Atualização de diagnóstico após exames complementares.

3. Exclusões (DELETE)
Remoção de um agendamento cancelado (sem consulta associada).
Exclusão de um medicamento obsoleto (que não é mais usado na clínica).
Remoção de um paciente "fantasma" (inserido apenas para teste, sem consultas).

Consultas SQL (SELECT)
Foram elaboradas 10 consultas que demonstram diferentes funcionalidades do SQL:
Filtros com WHERE e operadores lógicos
Ex.: Pacientes com alergia a penicilina ou amoxicilina.

Junções (JOIN) entre tabelas
Ex.: Listar receitas com medicamentos específicos.

Agregações (GROUP BY, COUNT, SUM, AVG)
Ex.: Média de valor das consultas por especialidade.

Subconsultas
Ex.: Consultas com valor acima da média.

Ordenação (ORDER BY)
Ex.: Médicos ordenados por quantidade de consultas.

Filtros em agrupamentos (HAVING)
Ex.: Medicamentos prescritos mais de uma vez.

Busca por padrões (LIKE)
Ex.: Pacientes com alergia a medicamentos específicos.

Relacionamentos complexos
Ex.: Receitas que contêm Losartana, com dados do paciente e médico.

Análise financeira
Ex.: Total recebido por forma de pagamento.

Controle de faltas
Ex.: Pacientes que não compareceram às consultas.
