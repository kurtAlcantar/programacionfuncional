![alt](https://imgs.search.brave.com/71ZpZYIDKJFF4hyzvZ_Ka3co-bXu5mS0uoIjcv5uvy4/rs:fit:1200:687:1/g:ce/aHR0cDovL3d3dy51/Y29sLm14L2NvbnRl/bnQvY21zLzkvaW1h/Z2UvVWRlQ0VDUlM4/MG4ucG5n)
#   *UNIVERSIDAD DE COLIMA*
## *FACULTAD DE INGENERIA MECANICA Y ELECTRICA*
#### *CARRERA: INGENIERIA EN COMPUTACION INTELIGENTE*
#### *Alumno: Christopher Kurt Alcantar Contreras*
#### *Profesor: Dr. Walter Alexander Mata López*
---
__Bienvenid@ a mi repositorio de github/Portafolio de tercera parcial__
En el obtendras todos los programas que realice en clases de programacion funcional
---
# Capitulo 6. Instalacion de Elixir y uso de Shell
## Funcion sin Argumentos
```elixir

# Funciones, una funcion siempre debe estar dentro de un modulo.
# Los nombres de funciones son igual que las variables.
# El nombre de una variable siempre inicia con un caracter alfabético en
# minúscula o caracter de subrayado (_)
# Después puede llevar cualquier combinación de estos caracteres
# La convención es usar solo letras, dígitos y subrayados
# Pueden terminar con los carateres ? o !.
# Por convención el ? se utiliza cuando la función retorna true o false
# El ! se utiliza generalmente en funciones que podrían provocar algún error en tiempo de ejecución
# Tanto defmodule como def NO son palabras reservadas del lenguaje, son macros


defmodule HolaMundo do
 def mensaje do
Fundamentos de programación funcional con Erlang y Elixir,
 IO.puts("Hola Mundo")
 end
end
```
---
## Funcion con argumentos
```elixir
defmodule Calculadora do
 def suma(n1,n2) do
 n1 + n2
 end
end
```
---
## Varios modulos dentro de un archivo
```elixir
defmodule Calculadora do
 def suma(n1,n2) do
 n1 + n2
 end
end
defmodule Areas do
 def area_cuadrado(l) do
 l*l
 end
end
```
---
## Reglas de los modulos  
```elixir
# Reglas de los módulos:
# -Inicia con una letra mayúscula
# -Se escribe con el estilo CamelCase
# -Puede consistir en caracteres alfanuméricos, subrayados y puntos (.).
# -Regularmente se usa para la organización jerárquica de los módulos. 

defmodule Geometria.Cuadrado do
 def perimetro(l) do
 4*l
 end
end
defmodule Geometria.Rectangulo do
 def perimetro(l1,l2) do
 2*l1 + 2*l2
 end
end
```
---
## Otra forma de anidar los modulos es la siguiente: 
```elixir
defmodule Geometria do
 defmodule Cuadrado do
 def perimetro(l) do
 4*l
 end
 end
 defmodule Rectangulo do
 def perimetro(l1,l2) do
 2*l1 + 2*l2
 end
 end
end
```
---
## Funciones expresadas de manera condensada
```elixir
defmodule Geometria do
 def perimetro_cuadrado(l), do: 4*l
 def perimetro_rectangulo(l1,l2), do: 2*l1 + 2*l2
end
```
---
## Invocaciones de una funcion interna
```elixir
defmodule Geometria do
 def perimetro1(l), do: cuadrado(l)
 def perimetro2(l), do: Geometria.cuadrado(l)
 def cuadrado(l), do: 4*l
end
```
---
## Visibilidad de funciones
```elixir
#-Se pueden utilizar funciones privadas con el constructor def
#-Función Publica y privada 

defmodule TestPublicoPrivado do
 def funcion_publica(msg) do
 IO.puts("#{msg} publico")
 funcion_privada(msg)
 end
 defp funcion_privada(msg) do
 IO.puts("#{msg} privado")
 end
end
TestPublicoPrivado.funcion_publica("este es un mensaje")
```
---
## Modulo geometria
```elixir
defmodule Geometria do
 def perimetro1(l), do: cuadrado(l)
 def perimetro2(l), do: Geometria.cuadrado(l)
 defp cuadrado(l), do: 4*l
end
```
---
## Operador pipeline
```elixir
#Obtener el cuadrado de la suma de 2 numeros (4 y 5)

defmodule Operaciones do
 def suma(n1,n2), do: n1 + n2
 def cuadrado(n), do: n * n
end
```
---
## Mediante un módulo test que realice las pruebas se podría realizar de la siguiente forma:
```elixir
defmodule Operaciones do
 def suma(n1,n2), do: n1 + n2
 def cuadrado(n), do: n * n
end
defmodule Test do
 def start do
 4 |> Operaciones.suma(5) |>Operaciones.cuadrado
 end
end
```
---
# Capitulo 7. Estructura del codigo en Elixir
## Polimorfismo(sobrecarga)
```elixir
defmodule Rectangulo do
 def area(l) do
 l * l
 end
 def area(l1,l2) do
 l1 * l2
 end
end
```
---
## Haciendo que una función dependa de otra de diferente aridad, se podría realizar lo siguiente:
```elixir
defmodule Calculadora do
 def suma(n) do
 suma(n,0)
 end
 def suma(n1,n2) do
 n1 + n2
 end
end
```
## Argumentos por defecto
```elixir
defmodule Calculadora do
 def suma(n1,n2 \\ 0) do
 n1 + n2
 end
end
#Se puede utilizar cualquier combinación de argumentos por defecto: 
defmodule Calculadora do
 def funcion(n1,n2 \\ 0, n3 \\ 1, n4, n5 \\ 2) do
 n1 + n2 + n3 + n4 + n5
 end
end
```
---
## Imports 
```elixir
import ModuloImportado
defmodule ModuloMain do
 def main do
 IO.puts("Funcion main")
 funcion_importada("Esta funcion es importada")
 end
end

#Creamosel Modulo a importar modsec.ex
#Escribimos el siguiente codigo: 

defmodule ModuloImportado do
 def funcion_importada(msg) do
 IO.puts(msg)
 end
end

#Si no se quiere importar el modulo, se puede utilizar de manera directa indicando el modulo y la funcion esto es:

defmodule ModuloMain do
 def main do
 IO.puts("Funcion main")
 ModuloImportado.funcion_importada("Esta funcion es importada")
 end
end
```
---
## Alias
```elixir
defmodule ModuloMain do
 alias ModuloImportado, as: MI

 def main do
 IO.puts("Funcion main")
 MI.funcion_importada("Esta funcion es importada con alias")
 end
end
```
---
## Atributos de modulo
```elixir
defmodule Geometria do
 @pi 3.141592
 def area(r) do
 r*r*@pi
 end
 def circunferencia(r) do
 2 * r * @pi
 end
end
```
---
## Secuencias de escape:
```elixir
IO.puts("1. Este es un mensaje")
IO.puts("2. Este es un \n mensaje")
IO.puts("3. Este es un \"mensaje\"")
IO.puts("4. Este es un \\mensaje\\")
IO.puts("5. Este \t es \tun \t mensaje")
IO.puts("4. Este
es un
mensaje")
```
---
## Concatenacion de Cadenas
```elixir
defmodule Cadena do
 def concatenar(cad1, cad2, separador \\ " ") do
 cad1 <> separador <> cad2
 end
end
Fundamentos de programación funcional con Erlang y Elixir,
IO.puts(Cadena.concatenar("Hola", "Mundo"))
IO.puts(Cadena.concatenar("Hola", "Mundo", "<->"))
```
---
## Funciones
```elixir
defmodule Calculadora do
 def div(_,0) do
 {:error, "No se puede dividir por 0"}
 end
 def div(n1, n2) do
Fundamentos de programación funcional con Erlang y Elixir,
 {:ok, "El resultado es: #{n1/n2}"}
 end
end
IO.inspect(Calculadora.div(5,0))
IO.inspect(Calculadora.div(5,3))
```
--- 
## Funciones invertidas
```elixir
defmodule Calculadora do
 def div(n1, n2) do
 {:ok, "El resultado es: #{n1/n2}"}
 end
 def div(_,0) do
 {:error, "No se puede dividir por 0"}
 end
end
IO.inspect(Calculadora.div(5,0))
IO.inspect(Calculadora.div(5,3))
```
---
## Guardas
``` elixir
defmodule Numero do
 def cero?(0), do: true
 def cero?(n) when is_integer(n), do: false
 def cero?(_), do: "No es entero"
end

IO.puts(Numero.cero?(0))
IO.puts(Numero.cero?(2))
IO.puts(Numero.cero?("3"))
```
--- 
## Condicionales
``` elixir
#EJEMPLO 1

defmodule Persona1 do
 def sexo(sex) do
 if sex == :m do
 "Masculino"
 else
 "Femenino"
 end
 end
end

#EJEMPLO 2

defmodule Persona2 do
 def sexo(sex) do
 if sex == :m do
 "Masculino"
 else if sex == :f do
 "Femenino"
Fundamentos de programación funcional con Erlang y Elixir,
 else
 "Sexo desconocido"
 end
 end
 end
end
```
---
## Case
``` elixir
defmodule Persona3 do
 def sexo(sex) do
 case sex do
 :m -> "Masculino"
 :f -> "Femenino"
 _ -> "Sexo desconocido"
 end
 end
end
```
## Match con funciones, ejemplo 1
``` elixir
defmodule Persona4 do
 def sexo(sex) when sex == :m do
 "Masculino"
 end
 def sexo(sex) when sex == :f do
 "Femenino"
 end
 def sexo(_sex) do
 "sexo desconocido"
 end
end
``` 
---
## Match con Funciones
``` elixir
defmodule Persona5 do
 def sexo(sex) when sex == :m, do: "Masculino"
 def sexo(sex) when sex == :f, do: "Femenino"
 def sexo(_sex), do: "sexo desconocido"
end
``` 
---
## Cond
``` elixir
defmodule Persona6 do
 def sexo(sex) do
 cond do
 sex == :m -> "Masculino"
 sex == :f -> "Femenino"
 true -> "Sexo desconocido"
 end
 end
end
``` 
---
# Capitulo 8. Herramienta mix
## Documentacion con ExDoc
``` elixir
defp deps do
 [
 {:ex_doc, "~>0.12"}
 ]
 end
``` 
---
## Case Ejemplo 1
``` elixir
defmodule Matematicas do
 def calculadora(opcion,{n1,n2}) do
 case opcion do
 "+" -> n1+n2
 "-" -> n1-n2
 "/" when n2 != 0 -> n1/n2
 "/" when n2 == 0 -> "No se puede dividir por 0"
 "*" -> n1*n2
 _ -> :error
 end
 end
end
IO.inspect Matematicas.calculadora("+",{5,4})
IO.inspect Matematicas.calculadora("-",{5,4})
IO.inspect Matematicas.calculadora("/",{5,4})
IO.inspect Matematicas.calculadora("/",{5,0})
IO.inspect Matematicas.calculadora("*",{5,4})
``` 
---
## Cond 
``` elixir
#Ejemplo 1
defmodule DiaSemana do
 def dia(d) do
 cond do
 d == 1 -> "Lunes"
 d == 2 -> "Martes"
 d == 3 -> "Miercoles"
 d == 4 -> "Jueves"
 d == 5 -> "Viernes"
 d == 6 -> "Sabado"
 d == 7 -> "Domingo"
 true -> "Dia no valido"
 end
 end
end
IO.puts DiaSemana.dia(1)
IO.puts DiaSemana.dia(2)
IO.puts DiaSemana.dia(3)
IO.puts DiaSemana.dia(4)
IO.puts DiaSemana.dia(5)
IO.puts DiaSemana.dia(6)
IO.puts DiaSemana.dia(7)
IO.puts DiaSemana.dia(8)

#Ejemplo 2

defmodule DiaSemana do
 def dia(d) do
 cond do
 d == "l" or d == "L" -> "Lunes"
 d == "ma" or d == "MA" -> "Martes"
 d == "mi" or d == "MI" -> "Miercoles"
 d == "j" or d == "J" -> "Jueves"
 d == "v" or d == "V" -> "Viernes"
 d == "s" or d == "S" -> "Sabado"
Fundamentos de programación funcional con Erlang y Elixir,
 d == "d" or d == "D" -> "Domingo"
 true -> "Dia no valido"
 end
 end
end
IO.puts DiaSemana.dia("l")
IO.puts DiaSemana.dia("ma")
IO.puts DiaSemana.dia("mi")
IO.puts DiaSemana.dia("j")
IO.puts DiaSemana.dia("v")
IO.puts DiaSemana.dia("s")
IO.puts DiaSemana.dia("d")
IO.puts DiaSemana.dia("L")
IO.puts DiaSemana.dia("MA")
IO.puts DiaSemana.dia("MI")
IO.puts DiaSemana.dia("J")
IO.puts DiaSemana.dia("V")
IO.puts DiaSemana.dia("S")
IO.puts DiaSemana.dia("D")
IO.puts DiaSemana.dia("Ma")
IO.puts DiaSemana.dia("mA")

#Ejemplo 3

defmodule DiaSemana do
 def dia(d) do
 d = String.upcase(d)
 cond do
 d == "L" -> "Lunes"
 d == "MA" -> "Martes"
 d == "MI" -> "Miercoles"
 d == "J" -> "Jueves"
 d == "V" -> "Viernes"
 d == "S" -> "Sabado"
 d == "D" -> "Domingo"
 true -> "Dia no valido"
 end
 end
end
IO.puts DiaSemana.dia("l")
IO.puts DiaSemana.dia("ma")
IO.puts DiaSemana.dia("mi")
IO.puts DiaSemana.dia("j")
IO.puts DiaSemana.dia("v")
IO.puts DiaSemana.dia("s")
IO.puts DiaSemana.dia("d")
IO.puts DiaSemana.dia("L")
IO.puts DiaSemana.dia("MA")
IO.puts DiaSemana.dia("MI")
IO.puts DiaSemana.dia("J")
IO.puts DiaSemana.dia("V")
IO.puts DiaSemana.dia("S")
IO.puts DiaSemana.dia("D")
IO.puts DiaSemana.dia("Ma")
IO.puts DiaSemana.dia("mA")

``` 
---
## Unless
``` elixir
#Ejemplo 1

defmodule MayorDeEdad do
 def mayor1(edad) do
 unless edad >= 18 do
 "Es menor de edad"
 end
 end
end

#Ejemplo 2

defmodule MayorDeEdad do
 def mayor1(edad) do
 unless edad >= 18 do
 "Es menor de edad"
 end
 end
 def mayor2(edad) do
 if edad < 18 do
 "Es menor de edad"
 end
 end
end
```
---
## Funciones Anonimas
```elixir
#Ejemplo 1

defmodule Calculadora do
 def suma(n1,n2), do: n1+n2
end
suma_anonima = fn(n1,n2) -> n1 + n2 end
IO.puts(Calculadora.suma(5,4))
IO.puts(suma_anonima.(5,5))

#Ejemplo 2

mayor? = fn(n1,n2) -> if n1 > n2 do true else false end end
IO.inspect(mayor?.(4,5))
IO.inspect(mayor?.(5,4))
IO.inspect(mayor?.(5,5))

#Ejemplo 3

mayor? = fn(n1,n2) -> if n1 > n2 do :si else :no end end
res = mayor?.(4,5)
IO.puts res
res = mayor?.(5,4)
IO.puts res

#Ejemplo 4

mayor = fn(n1,n2) ->
 if n1 > n2 do
 {:ok, "#{n1} > #{n2}"}
 else
 {:error, "#{n1} <= #{n2}"}
 end
end
IO.inspect mayor.(4,5)
IO.inspect mayor.(5,4)
IO.inspect mayor.(5,5)

#Ejemplo 5

mayor = fn(n1,n2) ->
 if n1 > n2 do
 {:ok, "#{n1} > #{n2}"}
 else
 {:error, "#{n1} <= #{n2}"}
 end
end
{status, res} = mayor.(4,5)
IO.puts status
IO.puts res
{status, res} = mayor.(5,4)
IO.puts status
IO.puts res
```
---
## Operador Pipe
```elixir
sum = 0
lista = [1,2,3,4,5]
lista = tl(lista)
IO.inspect(lista)
[num|lista] = lista
#para sacar el 2
IO.inspect(num)
IO.inspect(lista)
sum = sum + num
IO.inspect(sum)
#para sacar el 3
[num|lista] = lista
IO.inspect(num)
IO.inspect(lista)
sum = sum + num
IO.inspect(sum)
#para sacar el 4
[num|lista] = lista
IO.inspect(num)
IO.inspect(lista)
sum = sum + num
IO.inspect(sum)
#para sacar el 5
[num|lista] = lista
IO.inspect(num)
IO.inspect(lista)
sum = sum + num
IO.inspect(sum)
IO.puts("EL resultado es: #{sum*sum}")

#Solucion 1

defmodule PipeTest do
 def cuadrado(n), do: n*n
 def suma(lista) do
 Enum.sum(lista)
 end
end
IO.puts("#{PipeTest.cuadrado(PipeTest.suma(tl([1,2,3,4,5])))}")

#Solucion 2

defmodule PipeTest do
 def cuadrado(n), do: n*n
 def suma(lista) do
 Enum.sum(lista)
 end
 def csc(lista) do
 lista
 |> tl
 |> suma
 |> cuadrado
 end
end
IO.puts("#{PipeTest.csc([1,2,3,4,5])}")

```
---
## Herramienta de depuracio(debugging)
```elixir
ddefmodule PipeTest do
 def cuadrado(n), do: n*n
 def suma(lista) do
 Enum.sum(lista)
 end
 def csc(lista) do
 lista
 |> tl
 |> IO.inspect
 |> suma
 |> IO.inspect
 |> cuadrado
 end
end
IO.puts("#{PipeTest.csc([1,2,3,4,5])}")
```
---
## Ciclo for
```elixir
for x <- 1..10 do
 IO.puts(x)
end

#Ejemplo 2

sum = 0
for x <- 1..10 do
 sum = sum + x
end
IO.inspect(sum)

#Quitando sum para evitar los warnings

for x <- 1..10 do
 sum = sum + x
end
IO.inspect(sum)

#Asignando el for a la variable sum
#Eliminando el acumulador dentro del for

sum = for x <- 1..10 do
 x
end
IO.inspect(sum)

#Al saber que lo que genera es una lista, se puede utilizar la función sum del módulo Enum

sum = for x <- 1..10 do
 x
end
IO.puts Enum.sum(sum)

#Se puede expresar en una sola línea de código: 

IO.puts Enum.sum(1..10)
```







