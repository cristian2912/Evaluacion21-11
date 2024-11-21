
**EVALUACION HECHA POR CRISTIAN BELLO Y CARLOS CARDONA**
# CODIGO

```
def radix_sort(placas, matriculas):
    max_len = 6
    n = len(placas)

    for pos in range(max_len - 1, -1, -1):
        print(f"\nIteracion para la posicion {pos}:")

        temp_placas = ["" for _ in range(n)]
        temp_matriculas = [0] * n

        buckets = [[] for _ in range(256)]

        for i in range(n):
            char = placas[i][pos]
            buckets[ord(char)].append((placas[i], matriculas[i]))

        index = 0
        for bucket in buckets:
            for placa, matricula in bucket:
                temp_placas[index] = placa
                temp_matriculas[index] = matricula
                index += 1

        for i in range(n):
            placas[i] = temp_placas[i]
            matriculas[i] = temp_matriculas[i]

        print(f"Placas ordenadas: {placas}")
        print(f"Matriculas ordenadas: {matriculas}")


def busqueda_binaria(placas, matriculas, placa_buscada):
    izquierda, derecha = 0, len(placas) - 1
    while izquierda <= derecha:
        medio = (izquierda + derecha) // 2
        if placas[medio] == placa_buscada:
            return matriculas[medio]
        elif placas[medio] < placa_buscada:
            izquierda = medio + 1
        else:
            derecha = medio - 1
    return None

placas = ["JNT400", "QNA555", "AAA123", "CVY000", "QKA233", "MJO941", "BCM122"]
matriculas = [40010231, 5055178, 4891230, 14503098, 24353789, 39941452, 7841263]

radix_sort(placas, matriculas)

print("\nDatos ordenados:")
print("Placas:", placas)
print("Matriculas:", matriculas)

placa_buscada = "JNT400"
print(f"\nBuscando la matricula para la placa {placa_buscada}:")
matricula = busqueda_binaria(placas, matriculas, placa_buscada)
if matricula is not None:
    print(f"La matricula asociada es: {matricula}")
else:
    print(f"La placa {placa_buscada} no se encontro.")

```
