Relatório – Projeto do Sistema Bancário em C

Este projeto implementa um sistema bancário simples utilizando vetores e estruturas em linguagem C. 
O foco principal é permitir operações comuns como abertura de conta, depósito, saque, transferência, consulta, 
atualização de dados e encerramento de conta. A seguir, são descritas as principais decisões de implementação, 
validações e organização lógica do sistema.

Garantia de Unicidade do CPF

Para impedir que um mesmo cliente abra várias contas ativas com o mesmo CPF, foi implementada a função BuscarPorCPF(), 
que percorre o vetor de contas e compara o CPF informado com os já cadastrados. Durante a abertura de conta (abrirConta()), 
o sistema chama essa função e verifica se o CPF já está vinculado a uma conta ativa. Caso esteja, a abertura é bloqueada. 
Dessa forma, garante-se integridade e unicidade.

Modelagem e Estrutura dos Dados

Todas as contas são armazenadas em um vetor de estruturas Conta. A estrutura contém os campos essenciais: 
número, nome, CPF, agência, telefone, saldo e status (ativa ou encerrada). 
O número da conta e o código da agência são gerados automaticamente a partir da quantidade de contas cadastradas, 
evitando duplicidade e dispensando inserção manual.

O status da conta utiliza constantes (ATIVA e ENCERRADA) para facilitar comparações e garantir clareza no código.

Projeto das Funções

O sistema foi dividido em funções independentes, seguindo boa prática de modularização:

BuscarPorCPF / buscarConta → localizam contas por CPF ou por número + agência.

abrirConta → cria nova conta, valida CPF e inicializa saldo.

depositar / sacar / transferencias → operações financeiras com validação de saldo, entrada e status da conta.

consultar → busca dados por CPF ou por conta/agência.

alterar → permite atualizar telefone ou agência.

listarContas → filtra contas por status (ativas, encerradas, todas).

encerrarConta → só permite encerrar contas com saldo zerado.

A escolha de funções separadas busca facilitar manutenção, leitura e possíveis expansões futuras.

Validações Implementadas

O programa contém diversas validações importantes:

Entrada inválida (uso de scanf com verificação de retorno).

Contas encerradas não permitem operações (saque, depósito, transferência, alteração).

Depósitos e saques exigem valores positivos.

Saque e transferência verificam saldo insuficiente.

Encerramento de conta só é permitido com saldo igual a zero.

Busca rigorosa por número da conta + agência para evitar ambiguidades.

Remoção do \n de entradas via fgets() para evitar inconsistências.

Limite máximo de contas com mensagem apropriada.

Conclusão

O sistema foi desenvolvido com foco em organização, modularização e segurança das operações. 
As funções garantem isolamento lógico das tarefas, enquanto as validações impedem que o usuário execute ações incorretas 
ou inconsistentes. Assim, o programa atende aos requisitos básicos de um sistema bancário simples e fornece uma base sólida 
para futuras melhorias, como gravação em arquivos ou autenticação de usuário.
