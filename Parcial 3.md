```ruby
## Módulos en elixir 
      ### Gato se usa para comentar una sola linea
      defmodule Calculadora do #Nombre del modulo inicia con mayusculas
          def suma(n1,n2) do
            n1+n2
          end
          def resta(n1,n2) do #Cada función debe estar definada dentro de un modulo
            n1-n2
          end
          def multiplicacion(n1,n2) do #Nombre de la función inicia con minusculas
            n1*n2
          end
          #def division(_,0) do
            #"error divided by 0"
          #end
          def division(n1,n2) do
            n1/n2
          end


          #def test() do
            #IO.puts Calculadora.division(3,3)
            #IO.puts Calculadora.suma(3,4)
            #IO.puts Calculadora.resta(3,4)
            #IO.puts Calculadora.multiplicacion(3,4)
          #end
        end

        #Calculadora.test()

      defmodule Calculadora2 do
        def suma(n1,n2), do: n1+n2
        def resta(n1,n2), do: n1-n2
        def multiplicacion(n1,n2), do: n1*n2
        def division(n1,n2), do: n1/n2
      end

      defmodule HolaMundo do
        def imprimir_hola_mundo  do
          #IO.puts("Hola Mundo")
        end
      end
      defmodule HolaMundo2 do
        def saludo(msg)  do #Función con arguemntos, al momento de correr ponemos la función y dentro el mensaje
          IO.puts(msg)
        end
      end
      defmodule Calculadora do #Pipeline sirve para sumar con un solo valor, correr así: 4 |> Calculadora.suma(4)
          def suma(n1,n2) do
            n1+n2
          end
      end

      defmodule Areas do
        def area_cuadrado(l) do
          l*l
        end
      end

      defmodule Geometria.Cuadrado do #El punto entre medio del modulo es para organizar el codigo
        def perimetro(l) do
          4*l
        end
      end

      defmodule Geometria.Rectangulo do #Aún con el punto es el mismo modulo pero con diferetnte figura
        def perimetro(l1,l2) do
          2*l1 + 2*l2
        end
      end

      defmodule Geometria do #Se pueden anidar=Dentro de un modulo tener mas modulos
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

      defmodule Geometria1 do #Condensada: Reducir el código a una linea
        def perimetro_cuadrado(l), do: 4*l
        def perimetro_rectangulo(l1,l2), do: 2*l1 + 2*l2
        end

      defmodule Geometria2 do #Se pueden hacer invocaciones internas de una función
        def perimetro1(l), do: cuadrado(l) #Invoca a la función cuadrado declarada abajo
        def perimetro2(l), do: Geometria2.cuadrado(l) #Puede o no llevar prefijo del nombre del módulo
        def cuadrado(l), do: l*l
      end

      ## Encapsulación
      defmodule Geometria3 do
        def perimetro1(l), do: cuadrado(l) #Aquí si corre
        def perimetro2(l), do: Geometria3.cuadrado(l) #Aquí no corre por llamar al modulo
        defp cuadrado(l), do: l*l #Con de defp hacemos privada la función y no corre
      end

      defmodule TestPublicoPrivado do
        def funcion_publica(msg) do
          IO.puts("#{msg} publico") #Concatenar cadena con #{}
          funcion_privada(msg)
      end
        defp funcion_privada(msg) do
          IO.puts("#{msg} privado")
        end
      end
      #TestPublicoPrivado.funcion_publica("este es un mensaje")
   
   
      defmodule DistCalculator do
          def suma(n1,n2) do
              IO.puts(n1+n2)
          end
      end
      
      defmodule Operaciones do
          def suma(n1,n2), do: n1 + n2
          def cuadrado(n), do: n * n
      end
      defmodule Test do #realizar las pruebas
          def start do
          4 |> Operaciones.suma(5) |>Operaciones.cuadrado
          end
      end

      defmodule Rectangulo do
          def area(l) do #Aquí tenemos POLIMORFISMO porque tenemos 2 funciones con el mismo nombre pero diferente aridad
              l*l
          end
          def area(l1,l2) do
              l1 * l2
          end
      end

      defmodule Calculadora do #función que depende de otra de diferente aridad, se agrega un 0 para tener los 2 argumentos
          def suma(n) do
          suma(n,0) end
          def suma(n1,n2) do
               n1 + n2
          end
      end

      defmodule Calculadora2 do #Se pueden especificar argumentos por defecto
          def suma(n1,n2 \\ 0) do
          n1 + n2
          end
      end

      defmodule Calculadora3 do
          def funcion(n1,n2 \\ 0, n3 \\ 1, n4, n5 \\ 2) do
          n1 + n2 + n3 + n4 + n5
          end
      end
      
      import ModuloImportado
      defmodule ModuloMain1 do #importamos la función desde modsec.ex
          def main do
              IO.puts("Funcion main")
              funcion_importada("Esta funcion es importada")
          end
      end

      defmodule ModuloMain2 do #no importamos el módulo, utilizar de manera directa indicando el módulo y la función
        def main do
        IO.puts("Funcion main")
        ModuloImportado.funcion_importada("Esta funcion es importada")
        end
      end

      defmodule ModuloMain3 do
        alias ModuloImportado, as: MI
        def main do
        IO.puts("Funcion main")
        MI.funcion_importada("Esta funcion es importada con alias")
        end
      end

      defmodule ModuloImportado do
          def funcion_importada(msg) do
            IO.puts(msg)
          end
        end
## Documentación 
      #defmodule Geometria do
       #   @pi 3.141592 #atributos en tiempo de compilación
        #  def area(r) do
         #     r*r*@pi
          #end
          #def circunferencia(r) do
          #    2 * r * @pi
          #end
      #end

      defmodule Geometria2 do
        @moduledoc "Calcula el area y el perimetro de un circulo"

        @pi 3.141592

        @doc "calcula el area del circulo"
        def area(r), do: r*r*@pi

        @doc "calcula el perimetro de un circulo"
        def circunferencia(r), do: 2 * r * @pi
      end

## Secuencias de escape
      IO.puts("1. Este es un mensaje")
      IO.puts("2. Este es un \n mensaje")
      IO.puts("3. Este es un \"mensaje\"")
      IO.puts("4. Este es un \\mensaje\\")
      IO.puts("5. Este \t es \tun \t mensaje")
      IO.puts("6. Este
      es un
      mensaje")

      ### sigils
      IO.puts(~s("este es un ejemplo de sigil" apuntes de Elixir))
      IO.puts("Este \t es \tun \t mensaje")
      IO.puts(~S("Este \t es \tun \t mensaje"))

## Concatenación de cadenas
      defmodule Cadena do
        def concatenar(cad1, cad2, separador \\ " ") do
        cad1 <> separador <> cad2
        end
      end
      IO.puts(Cadena.concatenar("Hola", "Mundo"))
      IO.puts(Cadena.concatenar("Hola", "Mundo", "<->"))

## FUNCIONES
      defmodule Calculadora do
        def div(_,0) do
          {:error, "No se puede dividir por 0"}
        end
        def div(n1, n2) do
          {:ok, "El resultado es: #{n1/n2}"}
        end
      end
      IO.inspect(Calculadora.div(5,0))
      IO.inspect(Calculadora.div(5,3))

      defmodule Calculadora2 do #Aquí da error porque al poner la primera función toma la aridad /2
        def div(n1, n2) do #entonces cuando pasa al de abajo no lo deja ejecutarse porque solo necesita 1 arguemnto y tiene 2
          {:ok, "El resultado es: #{n1/n2}"}
        end
        def div(_,0) do
          {:error, "No se puede dividir por 0"}
        end
      end
      IO.inspect(Calculadora.div(5,0))
      IO.inspect(Calculadora.div(5,3))

## GUARDAS
      defmodule Numero do
        def cero?(0), do: true
        def cero?(n) when is_integer(n), do: false
        def cero?(_), do: "No es entero"
      end
      IO.puts(Numero.cero?(0))
      IO.puts(Numero.cero?(2))
      IO.puts(Numero.cero?("3"))

## CONDICIONALES
      ### if
      defmodule Persona1 do
        def sexo(sex) do
          if sex == :m do
            "Masculino"
          else        #Aquí puedes poner cualquier letra diferente a m y saldrá femenino
            "Femenino"
          end
        end
      end

      defmodule Persona2 do
        def sexo(sex) do
          if sex == :m do
            "Masculino"
          else if sex == :f do
            "Femenino"
          else #Aquí ya permite que solo sea m o f para masculino y femenino, si ejecuta otra letra lo marca como sexo desconocido
            "Sexo desconocido"
            end
          end
        end
      end

      ### case
      defmodule Persona3 do
        def sexo(sex) do
          case sex do
            :m -> "Masculino"
            :f -> "Femenino"
            _ -> "Sexo desconocido"
          end
        end
      end

      ### Match con funciones
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

      defmodule Persona5 do #código condensado
        def sexo(sex) when sex == :m, do: "Masculino"
        def sexo(sex) when sex == :f, do: "Femenino"
        def sexo(_sex), do: "sexo desconocido"
      end

      ### cond
      defmodule Persona6 do
        def sexo(sex) do
          cond do
            sex == :m -> "Masculino"
            sex == :f -> "Femenino"
            true -> "Sexo desconocido"
          end
        end
      end

      ### case
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

      ### cond
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

      defmodule DiaSemana2 do
        def dia(d) do
          cond do
            d == "l" or d == "L" -> "Lunes"
            d == "ma" or d == "MA"  -> "Martes"
            d == "mi" or d == "MI" -> "Miercoles"
            d == "j" or d == "J" -> "Jueves"
            d == "v" or d == "V" -> "Viernes"
            d == "s" or d == "S" -> "Sabado"
            d == "d" or d == "D" -> "Domingo"
            true -> "Dia no valido"
          end
        end
      end
      IO.puts DiaSemana2.dia("l")
      IO.puts DiaSemana2.dia("ma")
      IO.puts DiaSemana2.dia("mi")
      IO.puts DiaSemana2.dia("j")
      IO.puts DiaSemana2.dia("v")
      IO.puts DiaSemana2.dia("s")
      IO.puts DiaSemana2.dia("d")
      IO.puts DiaSemana2.dia("L")
      IO.puts DiaSemana2.dia("MA")
      IO.puts DiaSemana2.dia("MI")
      IO.puts DiaSemana2.dia("J")
      IO.puts DiaSemana2.dia("V")
      IO.puts DiaSemana2.dia("S")
      IO.puts DiaSemana2.dia("D")
      IO.puts DiaSemana2.dia("Ma")
      IO.puts DiaSemana2.dia("mA")

      defmodule DiaSemana3 do
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
      IO.puts DiaSemana3.dia("l")
      IO.puts DiaSemana3.dia("ma")
      IO.puts DiaSemana3.dia("mi")
      IO.puts DiaSemana3.dia("j")
      IO.puts DiaSemana3.dia("v")
      IO.puts DiaSemana3.dia("s")
      IO.puts DiaSemana3.dia("d")
      IO.puts DiaSemana3.dia("L")
      IO.puts DiaSemana3.dia("MA")
      IO.puts DiaSemana3.dia("MI")
      IO.puts DiaSemana3.dia("J")
      IO.puts DiaSemana3.dia("V")
      IO.puts DiaSemana3.dia("S")
      IO.puts DiaSemana3.dia("D")
      IO.puts DiaSemana3.dia("Ma")
      IO.puts DiaSemana3.dia("mA")

      ### unless
      defmodule MayorDeEdad do
        def mayor1(edad) do
          unless edad >= 18 do
            "Es menor de edad" #Al ejecutar si es mayor a 18 nos da nill porque no tiene que hacer nada mas
          end
        end
      end

      defmodule MayorDeEdad2 do
        def mayor1(edad) do #No ejecuta nada porque cuando es mayor a 18 no tiene que hacer
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

## Funciones anonimas: No tienen nombre, Se pueden fijar a variables
      defmodule Calculadora do
          def suma(n1,n2), do: n1+n2
      end
      suma_anonima = fn(n1,n2) -> n1 + n2 end
      IO.puts(Calculadora.suma(5,4))
      IO.puts(suma_anonima.(5,5))

      mayor? = fn(n1,n2) -> if n1 > n2 do true else false end end
      IO.inspect(mayor?.(4,5))
      IO.inspect(mayor?.(5,4))
      IO.inspect(mayor?.(5,5))

      ### Ejemplo con la salida personalizada
      mayor? = fn(n1,n2) -> if n1 > n2 do :si else :no end end
      IO.inspect(mayor?.(4,5))
      IO.inspect(mayor?.(5,4))

      mayor? = fn(n1,n2) -> if n1 > n2 do :si else :no end end
      res = mayor?.(4,5)
      IO.puts res
      res = mayor?.(5,4)
      IO.puts res

      mayor = fn(n1,n2) -> #Ejemplo con concatenación de cadenas y condicionales
        if n1 > n2 do
          {:ok, "#{n1} > #{n2}"}
        else
          {:error, "#{n1} <= #{n2}"}
        end
      end
      IO.inspect mayor.(4,5)
      IO.inspect mayor.(5,4)
      IO.inspect mayor.(5,5)

      ### Ejemplo 5
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

## Operador pipe
      ### Ejercicio que resuelve la suma de una lista y lo eleva al cuadrado
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

      ### Solución 1
      defmodule PipeTest do
        def cuadrado(n), do: n*n
        def suma(lista) do
          Enum.sum(lista)
        end
      end
      IO.puts("#{PipeTest.cuadrado(PipeTest.suma(tl([1,2,3,4,5])))}")

      ### Solución 2
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

## Herramienta de depuración (debugging)
      defmodule PipeTest do
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

## Ciclo for
      ### Ejemplo contar del 1 al 10
      for x <- 1..10 do
        IO.puts(x)
      end

      ### Ejemplo: sumar todos los numeros entre 1 y 10
      #sum = 0 Se quita la suma para evitar los warnings
      for x <- 1..10 do
        sum = sum + x
      end
      IO.inspect(sum)

      ### Ejemplo: Asignando el for a la variable sum
      sum = for x <- 1..10 do
        x
      end
      IO.inspect(sum)

      #Al saber que genera una lista podemos sumarla con Enum
      sum = for x <- 1..10 do
        x
      end
      IO.puts Enum.sum(sum)

      ### Ejemplo con código condensado: una sola línea de código
      IO.puts Enum.sum(1..10)

## EJERCICIOS DE RECURSIÓN

      ### Programa recursivo que imprima n veces un mensaje
      defmodule Repetir do
      def imprimir(msg, n) when n<= 1 do
          IO.puts("#{n}: #{msg}")
      end
      def imprimir(msg, n) do
          IO.puts("#{n}: #{msg}")
          imprimir(msg, n-1)
          end
      end
      Repetir.imprimir("Hola",10)

      ### Programa que invierte el orden de los números
      defmodule Repetir do
        def imprimir(msg, n,ls) when n>= ls do
          IO.puts("#{n}: #{msg}")
        end
        def imprimir(msg, n,ls) do
          IO.puts("#{n}: #{msg}")
          imprimir(msg, n+1,ls)
        end
      end
      Repetir.imprimir("Hola",1,10)

      ### Programa recursivo que sume todos los elementos de una
      # serie de números en una lista
      defmodule Matematicas do
        def sum_list([], suma), do: suma
        def sum_list([head|tail], suma) do
            sum_list(tail, suma+head)
        end
      end
      IO.puts(Matematicas.sum_list([1,2,3,4,5,6,7,8,9,10],0))
      IO.puts(Matematicas.sum_list([1,3,5,7,9,10,15],0))

      ### Programa que obtiene el promedio de 10 calificaciones
      # entre 0 y 10 almacenadas en una lista
      defmodule Matematicas2 do
        def sum_list([], suma), do: suma
        def sum_list([head|tail], suma) do
            sum_list(tail, suma+head)
        end
      end
      IO.puts(Matematicas2.sum_list([10,5,9,9,8,5,7,9,6,5],0)/10)

      ### Programa que crear una función promedio que calcule el
      # promedio de 10 calificaciones almacenadas en una lista entre 0 y 10
      defmodule Matematicas3 do
        def sum_list([], suma), do: suma
        def sum_list([head|tail], suma) do
            sum_list(tail, suma+head)
        end
        def promedio(calificaciones, n) do
          sum_list(calificaciones,0)/n
        end
      end
        IO.puts(Matematicas3.promedio([10,5,9,9,8,5,7,9,6,5],10))

      ### Programa que calcula el promedio de n calificaciones entre 0 y 10 en una lista
      defmodule Matematicas4 do
        def sum_list([], suma), do: suma
        def sum_list([head|tail], suma) do
            sum_list(tail, suma+head)
          end
        def promedio(calificaciones) do
          sum_list(calificaciones,0)/Enum.count(calificaciones)
        end
      end
      IO.puts(Matematicas4.promedio([10,5,9,9,8,5,7,9,6,5]))

      # Usando el módulo Enum
      calificaciones = [10,5,9,9,8,5,7,9,6,5]
      IO.puts Enum.sum(calificaciones)/Enum.count(calificaciones)

      ### Programa que genera n calificaciones aleatorias entre 0 y 10 y obtener su promedio
      max = 50
      calificaciones = for _x <- 1..max do
        Enum.random(0..10)
      end
      IO.inspect(calificaciones)
      IO.puts Enum.count(calificaciones)
      IO.puts Enum.sum(calificaciones)/Enum.count(calificaciones)

      # Escriba el problema anterior con un módulo y una función,
      # recibiendo como argumentos la cantidad de calificaciones a generar,
      # así como el rango de calificaciones.

      defmodule Estadistica do
        def promedio(max_cal, _li, _ls) when max_cal <= 1 do
          :error
        end
        def promedio(max_cal, li, ls) when max_cal > 1 do
          calificaciones = for _x <- 1..max_cal do
            Enum.random(li..ls)
          end
          Enum.sum(calificaciones)/Enum.count(calificaciones)
        end
      end
      IO.puts Estadistica.promedio(50,1,15)
      IO.puts Estadistica.promedio(-5,1,15)

      ### Programa recursivo que cuente de manera creciente de
      ### li (límite inferior) a ls (límite superior) para li>=ls inclusive

      defmodule For_range do
        def for_to(n,ls) when n > ls do
          IO.puts "error"
        end
        def for_to(n,ls) when n >= ls do
          IO.puts n
        end
        def for_to(n,ls) do
            IO.puts n
            for_to(n + 1,ls)
        end
      end
      IO.puts("Contar de 1 a 10")
      For_range.for_to(1,10)
      IO.puts("Contar de 12 a 5")
      For_range.for_to(12,5)

      ### Programa que sume los valores de los números consecutivos
      ### entre li y ls inclusive

      defmodule For_range do
        def for_to(n,ls) when n >= ls do
          n
        end
        def for_to(n,ls) do
          n + for_to(n + 1,ls)
        end
      end
      
        IO.puts("suma de los numeros de 1 a 10")
        IO.puts For_range.for_to(1,10)
        IO.puts("suma de los numeros 5 a 12")
        IO.puts For_range.for_to(5,12)
```
