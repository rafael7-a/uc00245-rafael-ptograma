 
import ipaddress
import random
import time

print("==============================")
print("       NETWORK MANAGER")
print("==============================")

while True:

    print("\n===== MENU PRINCIPAL =====")
    print("1 - Verificar endereço IP")
    print("2 - Identificar classe IP")
    print("3 - Testar ligação (PING)")
    print("4 - Simular Firewall")
    print("5 - Sair")

    opcao = input("\nEscolhe uma opção: ")

    if opcao == "1":

        ip = input("Introduz um endereço IP: ")

        try:
            endereco = ipaddress.ip_address(ip)

            print("\nEndereço IP válido!")

            if endereco.is_private:
                print("Tipo: IP privado")
            else:
                print("Tipo: IP público")

        except ValueError:
            print("Endereço IP inválido!")

    elif opcao == "2":

        ip = input("Introduz um endereço IP: ")

        try:
            primeiro = int(ip.split(".")[0])

            if 1 <= primeiro <= 126:
                print("Classe A")

            elif 128 <= primeiro <= 191:
                print("Classe B")

            elif 192 <= primeiro <= 223:
                print("Classe C")

            elif 224 <= primeiro <= 239:
                print("Classe D")

            elif 240 <= primeiro <= 255:
                print("Classe E")

            else:
                print("Endereço inválido!")

        except:
            print("IP inválido!")

    elif opcao == "3":

        ip = input("Introduz o IP de destino: ")

        print("\nA testar ligação...")

        time.sleep(2)

        resultado = random.choice([True, False])

        if resultado:
            print("Resposta recebida!")
            print("Ligação estabelecida.")
        else:
            print("Tempo limite excedido.")
            print("Sem resposta do destino.")

    elif opcao == "4":

        origem = input("O IP de origem é interno? (sim/nao): ")
        porta = input("Introduz a porta de destino: ")

        if origem.lower() == "sim" and porta == "443":
            print("FIREWALL: ACESSO PERMITIDO")

        else:
            print("FIREWALL: ACESSO BLOQUEADO")

    elif opcao == "5":

        print("A terminar o Network Manager...")
        break

    else:
        print("Opção inválida! Tenta novamente.")

print("Programa terminado.")

