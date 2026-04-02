import sys

def converter_comprimento(valor, opcao):
    # 1 km = 0.621371 milhas
    if opcao == '1': return valor * 0.621371, "milhas"
    if opcao == '2': return valor / 0.621371, "quilômetros"

def converter_massa(valor, opcao):
    # 1 kg = 2.20462 libras
    if opcao == '1': return valor * 2.20462, "libras"
    if opcao == '2': return valor / 2.20462, "quilogramas"

def converter_temperatura(valor, opcao):
    if opcao == '1': # Celsius para Fahrenheit
        res = (valor * 9/5) + 32
        return res, "°F"
    if opcao == '2': # Fahrenheit para Celsius
        res = (valor - 32) * 5/9
        return res, "°C"

def menu():
    print("\n" + "="*30)
    print("      UNIT CONVERTER 1.0")
    print("="*30)
    print("1. Comprimento (Km <-> Milhas)")
    print("2. Massa (Kg <-> Libras)")
    print("3. Temperatura (°C <-> °F)")
    print("0. Sair")
    return input("\nEscolha uma categoria: ")

def main():
    while True:
        cat = menu()
        
        if cat == '0':
            print("Saindo... Até a próxima conversão!")
            break
            
        if cat not in ['1', '2', '3']:
            print("Opção inválida!")
            continue

        try:
            print("\nSub-opções:")
            if cat == '1':
                print("1. Km para Milhas\n2. Milhas para Km")
                func = converter_comprimento
            elif cat == '2':
                print("1. Kg para Libras\n2. Libras para Kg")
                func = converter_massa
            elif cat == '3':
                print("1. Celsius para Fahrenheit\n2. Fahrenheit para Celsius")
                func = converter_temperatura

            op = input("Escolha a direção: ")
            val = float(input("Digite o valor original: "))
            
            resultado, unidade = func(val, op)
            print(f"\n✅ Resultado: {val} convertido é {resultado:.2f} {unidade}")
            
        except ValueError:
            print("\n❌ Erro: Por favor, insira valores numéricos válidos.")
        except TypeError:
            print("\n❌ Erro: Opção de conversão inválida.")

if __name__ == "__main__":
    main()
