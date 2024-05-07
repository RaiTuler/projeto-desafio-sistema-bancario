#desafio bancario
#deposito de valores positivos e armazenar no extrato 
#3 saques por dia de no maximo R$500
#caso nao tenha saldo deve exibir uma mensagem informando
#saques tbm sao armazenados no extrato
#extrato deve listar saques e depositos e informar o saldo em conta 

class Sistema():
    def __init__(self):
        self.saldo = 1000
        self.limite = 500 
        self.extrato = []
        self.contador = 0
    def deposito(self, valor_deposito):
        if valor_deposito > 0:
            self.saldo += valor_deposito
            self.extrato.append(('deposito',valor_deposito))
            print('deposito de R$',valor_deposito,'realizado')
        else: print('deposite um valor maior que 0')
    def saque(self, valor_saque):
            if self.contador < 3:
                if valor_saque <= self.saldo and valor_saque <= self.limite:
                    self.saldo -= valor_saque
                    self.extrato.append(('saque',valor_saque))
                    self.contador += 1
                    print('saque de R$',valor_saque,'realizado')
                    print('são permitidos apenas 3 saques diarios, ja foram feitos:',self.contador)
                else: 
                    print('saldo ou limite de saldo indisponivel')
                
                
            else: print('limite de saques alcançado')
            
        
    def mostrar_extrato(self):
        print('extrato:')
        for op in self.extrato:
            print(f'{op[0]}: R${op[1]}')
        print(f'Saldo em conta: R${self.saldo}')
sistema = Sistema()
while True:
    try:
        operacao = (int(input('''
        1 = depositar
        2 = sacar
        3 = ver extrato
        4 = sair
        escolha uma operação:''')))
        if operacao == 1:
            valor_deposito = (int(input('digite o valor do deposito: ')))
            sistema.deposito(valor_deposito)
        elif operacao == 2:
            valor_saque = (int(input('digite o valor que deseja sacar: ')))
            sistema.saque(valor_saque)
        elif operacao == 3:
            sistema.mostrar_extrato()
        elif operacao == 4:
            print ('saiu')
            break
        else: 
            print('digite uma opção valida')
    except ValueError:
        print('Por favor, digite apenas digitos.')
