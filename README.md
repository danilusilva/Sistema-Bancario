# SystemBank

[![Python Version](https://img.shields.io/badge/python-3.x-blue.svg)](#)  
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Sistema bancário simples em Python que simula operações básicas de conta corrente, com suporte a múltiplos clientes e contas.

---

## 💰 Funcionalidades

- **Cadastro de Cliente**: Registro de clientes Pessoa Física, com nome, CPF, data de nascimento e endereço.  
- **Criação de Conta**: Associação de uma ou mais contas correntes a cada cliente.  
- **Depósito**: Adiciona valores ao saldo da conta, validando valores positivos.  
- **Saque**: Realiza saques com validação de:
  - Saldo suficiente  
  - Limite máximo de valor por saque  
  - Quantidade máxima de saques diários  
- **Extrato**: Exibição do histórico de transações (saques e depósitos) e saldo atual.  
- **Listagem de Contas**: Mostra detalhes de todas as contas criadas.  
- **Menu Interativo**: Navegação por opções via terminal.

---

## 🧠 Estrutura de Classes

- **Cliente (Base)**
  - Armazena `endereco` e lista de `contas` associadas.  
  - Métodos para realizar transações e adicionar contas.

- **PessoaFisica (Cliente)**
  - Atributos: `nome`, `data_nascimento`, `cpf` e `endereco`.

- **Conta (Base)**
  - Atributos internos: `_saldo`, `_numero`, `_agencia`, `_cliente`, `_historico`.  
  - Propriedades: `saldo`, `numero`, `agencia`, `cliente`, `historico`.  
  - Métodos:
    - `sacar(valor)`: validações básicas.  
    - `depositar(valor)`: valida valor positivo.  
  - Fábrica `nova_conta()` para criar novas contas.

- **ContaCorrente (Conta)**
  - Adiciona: `_limite` (valor máximo por saque) e `_limite_saques` (quantidade diária).  
  - `sacar()`: sobrescrita para checar limites antes do saque.  
  - `__str__()`: formatação amigável na listagem.

- **Historico**
  - Mantém lista de transações.  
  - `adicionar_transacao()`: registra tipo, valor e timestamp (`%d-%m-%Y %H:%M:%S`).

- **Transacao (ABC)**
  - Propriedade abstrata `valor`.  
  - Método abstrato `registrar(conta)`.

- **Saque (Transacao)** e **Deposito (Transacao)**
  - Implementam `registrar()`, chamando `conta.sacar()` ou `conta.depositar()` e registram no histórico.

---

## 🚀 Como Executar Localmente

1. Garanta ter o Python 3 instalado.  
2. Clone o repositório ou baixe este arquivo.  
3. No terminal, execute:

   ```bash
   python systembank.py
