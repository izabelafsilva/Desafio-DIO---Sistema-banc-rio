#Menu de seleção do usuário
menu = """

[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair

=> """

#Condições do banco
saldo = 0
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3

while True:

    opcao = input(menu) #Mostra o menu para o usuário escolher a opção que deseja efetuar

    if opcao == "d": #Depositar
        valor = float(input("Valor do depósito: "))

        if valor > 0: #Valor precisa ser maior que zero
            saldo += valor #Adiciona ao saldo
            extrato += f"Depósito: R$ {valor:.2f}\n" "Adiciona linha ao extrato

        else:
            print("ERRO: Valor inválido.") #Caso informe número menor que zero

    elif opcao == "s": #Sacar
        valor = float(input("Valor do saque: "))

        excedeu_saldo = valor > saldo

        excedeu_limite = valor > limite

        excedeu_saques = numero_saques >= LIMITE_SAQUES

        if excedeu_saldo:
            print("ERRO: Saldo insuficiente.")

        elif excedeu_limite:
            print("ERRO: Limite de saque de R$500,00.")

        elif excedeu_saques:
            print("ERRO: Número de saques excedido.")

        elif valor > 0:
            saldo -= valor #Subtrai o valor sacado do saldo da conta
            extrato += f"Saque: R$ {valor:.2f}\n" #Adiciona linha ao extrato
            numero_saques += 1 #Incrementa quantidade de saque

        else:
            print("ERRO: Valor inválido.") #Se informar número menor que zero

    elif opcao == "e": #Exibir extrato
        print("\n================ EXTRATO ================")
        print("Sem movimentações." if not extrato else extrato) #Caso não tenham entradas no extrato
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("==========================================")

    elif opcao == "q": #Sair
        break

    else:
        print("ERRO: Selecione uma opção válida.") #Se o cliente não selecionar nenhuma das opções apresentadas
