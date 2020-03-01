
# Diseño de bancos de memorias para uC 8051
## DESCRIPCION PROYECTO
Configuración de solo direccionamiento externo del uC 8051, utilizando un banco de memoria 12kx8 con tres memorias ROM 4kx8 y una memoria RAM 2kx8. El circuito debe almacenar el código de programa en la memoria ROM 0. Ambas memorias deben empezar en la dirección 0x0000. Se agregó un led en parpadeo en el P1 de uC para comprobar el funcionamiento del condigo. 

#3 OBJETIVO DEL PROYECTO
Poner a prueba la habilidad de diseño de bancos de memoria para trabajar con el 8051, configurar de manera correcta el 8051, de forma  que pueda ser capaz de direccionar el código de modo externo y  quemar el archivo  .hex en la memoria para que proteus pueda simular en circuito habilitando la opción de fetching en el micro.

## RECURSOS A UTILIZAR
Para este circuito se disponen solo de memorias EEPROM 4kx8 para en banco de memoria ROM y memorias SRAM 2k8 para la memoria RAM, se utiliza un latch 74HC373 para el arreglo del puerto P0, leds y resistencias además del cristal de 12Mhz para el reloj del uC con sus capacitores.
1-uC 80C51
3-Memorias eeprom 2732
1-Memoria sram 6116
1-Latch 74hc737
-Dispositivos pasivos, resistencias, capacitores, etc..

## TABLA DE DIRECCIONAMIENTO 
Esta tabla muestra el direccionamiento de todas la memorias y como están ubicadas en el banco de memoria.

A15|	A14|	A13|	A12|	A11|	A10|	A09|	A08|	A07|	A06|	A05|	A04|	A03|	A02|	A01|	A0|	HEXA|	MEMORIA
0	0	0	0	0	0	0	0	0	0	0	0	0	0	0	0	0X0000	MEMORIA
RAM
0	0	0	0	0	1	1	1	1	1	1	1	1	1	1	1	0X07FF	
0	0	0	0	0	0	0	0	0	0	0	0	0	0	0	0	0X0000	MEMORIA
ROM 0
0	0	0	0	1	1	1	1	1	1	1	1	1	1	1	1	0X0FFF	
0	0	0	1	0	0	0	0	0	0	0	0	0	0	0	0	0X1000	MEMORIA
ROM 1
0	0	0	1	1	1	1	1	1	1	1	1	1	1	1	1	0X1FFF	
0	0	1	0	0	0	0	0	0	0	0	0	0	0	0	0	0X2000	MEORIA 
ROM 2
0	0	1	0	1	1	1	1	1	1	1	1	1	1	1	1	0X2FFF	


RAM	ROM	Tamaño
	0x2FFF

0x2000	4K
ROM 2
	0x1FFF

0x1000	4K
ROM 1

	0x0FFF

0x0000	2K
ROM0
0x07FF
0x0000		2K
RAM	2K
ROM 0


## DISENO ESQUEMATICO
Este diagrama muestra cómo debe conectarse el micro 8051 en modo de direccionamiento externo con un banco de memoria ROM 12kx8 y R AM2kx8. El reto más difícil fue la conexión ya que hay que separar el bus de datos del bus de direcciones y ambos corresponden al P0, así que tomando solo las direcciones después del latch se elimina este problema, además de que la señal de oe del latch debe permanecer fija a tierra.



## CONCLUSION
Los bancos de memoria nos proporcionan un diseño más robusto y de mayor tamaño al no depender de la capacidad ilimitada del micro, además podemos ser más puntuales con el manejo del código y las variables.
