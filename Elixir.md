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

# Secuencias de escape:
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
# Concatenacion de Cadenas
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
# Funciones
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
# Funciones invertidas
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
# Guardas
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
# Condicionales
``` elixir
@EJEMPLO 1

defmodule Persona1 do
 def sexo(sex) do
 if sex == :m do
 "Masculino"
 else
 "Femenino"
 end
 end
end

@EJEMPLO 2

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









