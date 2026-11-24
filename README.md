# Contador de Domingos en el Siglo XX (1901–2000)

Programa en **Python** que calcula cuántos **domingos cayeron en el día 1 de cada mes** entre el **1 de enero de 1901 y el 31 de diciembre de 2000**, simulando el calendario día por día desde el 1 de enero de 1900.

## Código

```python
domingo = 0
for año in range(1900, 2001):
    for mes in range(1, 13):
        if mes == 2:
            if (año % 4 == 0 and año % 100 != 0) or (año % 400 == 0):
                dias = 29
            else:
                dias = 28
        elif mes in [4, 6, 9, 11]:
            dias = 30
        else:
            dias = 31

        for dia in range(1, dias + 1):
            if año == 1900 and mes == 1 and dia == 1:
                dia_semana = 1
            else:
                dia_semana = (dia_semana + 1) % 7

            if dia_semana == 0 and dia == 1 and año >= 1901:
                domingo += 1
print(f"Total domingos hasta ahora: {domingo}")
```

## Explicación parte por parte

* **Contador y bucles principales (`domingo`, `año`, `mes`)**: `domingo = 0` guarda el conteo total. `for año in range(1900, 2001)` recorre de `1900` a `2000` (usando `1900` como referencia inicial), y `for mes in range(1, 13)` recorre los 12 meses.
* **Días del mes y bisiestos (`if mes == 2...`)**: En febrero (`2`) revisa si el año es bisiesto (divisible entre `4` y no entre `100`, o divisible entre `400`) para asignar `29` o `28` días. Asigna `30` días a abril, junio, septiembre y noviembre (`[4, 6, 9, 11]`), y `31` al resto.
* **Recorrido de días y día de la semana (`dia_semana`)**: `for dia in range(1, dias + 1)` itera cada día del mes. El `1900-01-01` fija `dia_semana = 1` (lunes), y los demás días avanzan con `(dia_semana + 1) % 7` en un ciclo de `0` a `6` (`0` = domingo).
* **Conteo e impresión final (`if dia_semana == 0...`, `print`)**: Suma `1` a `domingo` solo cuando cae domingo (`0`), es día `1` y el año es `1901` o mayor (`año >= 1901`). Al terminar, imprime el resultado total.
