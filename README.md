# Modelando_o_Sistema_Bancario_em_POO_com_Python
Neste desafio foi elaborada a implementação do sistema bancário, para armazenar os dados de clientes e contas bancárias em objetos ao invés de dicionários, o código usado foi o modelo de classes UML.

Segue abaixo os códigos em POO em Python com o modelo de classes UML:

# Definindo a classe Cliente
class Cliente:
    def __init__(self, nome, cpf):
        self.nome = nome
        self.cpf = cpf

    def __str__(self):
        return f'Cliente: {self.nome}, CPF: {self.cpf}'


# Definindo a classe Conta Bancária
class ContaBancaria:
    def __init__(self, numero, cliente, saldo=0):
        self.numero = numero
        self.cliente = cliente
        self.saldo = saldo

    def deposito(self, valor):
        if valor > 0:
            self.saldo += valor
            print(f'Depósito de R${valor} realizado com sucesso. Novo saldo: R${self.saldo}')
        else:
            print('Valor de depósito inválido.')

    def saque(self, valor):
        if valor > 0 and valor <= self.saldo:
            self.saldo -= valor
            print(f'Saque de R${valor} realizado com sucesso. Novo saldo: R${self.saldo}')
        else:
            print('Valor de saque inválido ou saldo insuficiente.')

    def extrato(self):
        print(f'Número da conta: {self.numero}')
        print(f'Titular da conta: {self.cliente.nome}')
        print(f'Saldo atual: R${self.saldo}')


# Exemplo de uso
if __name__ == "__main__":
    cliente1 = Cliente("João", "123.456.789-00")
    conta1 = ContaBancaria("001", cliente1)

    cliente2 = Cliente("Maria", "987.654.321-00")
    conta2 = ContaBancaria("002", cliente2)

    conta1.deposito(1000)
    conta2.deposito(1500)

    conta1.saque(500)
    conta2.saque(200)

    conta1.extrato()
    conta2.extrato()
