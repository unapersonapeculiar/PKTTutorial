Introduccion:

Este manual cubre los aspectos básicos para comenzar a trabajar con Cisco Packet Tracer. Para una comprensión más profunda y para casos de uso más avanzados, es recomendable consultar la documentación oficial de Cisco y otros recursos educativos especializados como puede ser la academia online de cisco skill for all.
### 1. Explicación de la Interfaz Gráfica del Packet Tracer

La interfaz gráfica de Cisco Packet Tracer se divide en varias áreas principales:

- **Área de Trabajo:** Es el espacio grande en el centro de la pantalla donde se diseñan y visualizan las redes.![[src/img/Pasted image 20240207154633.png]]
---
- **Dispositivos y Componentes:** abajo al lado izquierdo, encontrarás la lista de dispositivos y componentes que puedes arrastrar al área de trabajo. Estos están organizados en categorías como Routers, Switches, Dispositivos finales, etc.
![[src/img/Pasted image 20240207154717.png]]
- **Propiedades del dispositivo:** Al hacer clic en un dispositivo, se muestra la vista de interfaces que tiene el dispositivo
![[src/img/Pasted image 20240207154830.png]]
---

- **Barra de Herramientas:** En la parte superior, se encuentra la barra de herramientas que ofrece acceso rápido a funciones como guardar, abrir, copiar, pegar, deshacer, entre otras.
![[src/img/Pasted image 20240207154857.png]]
---

- **Modos de Simulación y Tiempo Real:** En la esquina inferior derecha, puedes cambiar entre los modos de simulación y tiempo real.
	![[src/img/Pasted image 20240208214929.png]]
---
### 2. Conectar Dos Equipos Usando Cables de Red Adecuados

Para conectar dos equipos (por ejemplo, un PC con un switch o dos PCs directamente):

1. Selecciona el cable adecuado que se ubica en la sección de abajo a mano  izquierda, 
	![[src/img/Pasted image 20240207155214.png]]
2. normalmente se selecciona un cable de par trenzado  para conectar dispositivos diferentes (PC a switch) o un cable cruzado para dispositivos iguales (PC a PC) tambien existe cable serial , fibra optica que estos no lo vamos a usar de momento
	![[src/img/Pasted image 20240207155244.png]]
1. Haz clic en el primer dispositivo, elige el puerto (Normalmente Fastethernet 0).
![[src/img/Pasted image 20240207155306.png]]
3. Haz clic en el segundo dispositivo y selecciona el puerto (los mas bajo(1,2,3,4,5) se utiliza para los ordenador y dispositvos varios y los mas altos para conectar router y switch (20,21,22,23,24) ).
	![[src/img/Pasted image 20240207155336.png]]
4. Resultado Final
	![[src/img/Pasted image 20240207155651.png]]
---

### 3. Diferenciar Entre Realtime y Simulation

- **Realtime:** En este modo, la red opera en tiempo real. Las modificaciones en la configuración de los dispositivos tienen efecto inmediatamente. Es útil para probar y observar el comportamiento de la red en condiciones normales de operación.
	![[src/img/Pasted image 20240207155941.png]]
---
- **Simulation:** Permite observar cómo los datos se mueven a través de la red y cómo se procesan los protocolos en cada paso. Es ideal para fines educativos y para entender detalladamente el funcionamiento de las redes.
	![[src/img/Pasted image 20240207160047.png]]
	![[src/img/Pasted image 20240207161456.png]]
---
# 4. Abreviaturas y trucos variados - Por ampliar 

*Existen comandos que no funcionan en el modo configurador que se usan en el modo normal (en el CLI tal cual sin enable)

| Abreviaturas | Comando Completo | Descripción |
| ---- | ---- | ---- |
| conf t | configure terminal | Accede al modo de configuración global. |
| int | interface | Accede a la configuración de una interfaz específica. |
| sh | show | Muestra configuraciones o estado de los protocolos y conexiones. |
| sh run | show running-config | Muestra la configuración actualmente activa en el dispositivo. |
| sh ip int br | show ip interface brief | Muestra un resumen de las interfaces, incluyendo sus IPs. |
| en | enable | Cambia al modo privilegiado. |
| no | (negación) | Utilizado para deshacer comandos o desactivar configuraciones. |
| end | (salir de modo configuración) | Regresa al modo EXEC privilegiado desde cualquier modo de configuración. |
| wr | write | Guarda la configuración en la memoria NVRAM. |
| exit | (salir) | Sale del modo actual o cierra la sesión de terminal. |
NOTA: Existen mas abreviaturas pero os he colocado las mas usadas

Tabulacion:

para completar un comando como linux podemos usar el tabulador
![[src/img/Pasted image 20240207163142.png]]
---

### 4. Cómo Entrar al Modo Configurador global de un Switch y un Router
**Estos comandos son universales**
#### Switch o Router:

1. Haz clic en el dispositivo.
![[src/img/Pasted image 20240207162211.png]]
2. Selecciona la pestaña "CLI" para acceder al modo de línea de comandos.
![[src/img/Pasted image 20240207162222.png]]
3. Puede que necesites presionar "Enter" para activar el prompt de comandos.
![[src/img/Pasted image 20240207162236.png]]
4. Escribir la palabra "enable" para entrar al modo administrador
![[src/img/Pasted image 20240207162249.png]]
5. Escribir el comando "Configure terminal" para empezar a configurar cosas varias del dispositivo .
![[src/img/Pasted image 20240207162334.png]]



### 5. Asignar una IP a una Interfaz en Concreto en un Router

1. Accede al modo de configuración del router (CLI).
2. Entra en el modo de configuración global con el comando `enable` seguido de `configure terminal` (Visto anteriormente no realizar capturas)
3. Accede a la interfaz específica con el comando `interface [tipo de interfaz][número de interfaz]`. Por ejemplo, `interface FastEthernet0/0`.
4. Asigna la dirección IP con el comando `ip address [dirección IP] [máscara de subred]`. Por ejemplo, `ip address 192.168.1.1 255.255.255.0`.
5. Activa la interfaz con el comando `no shutdown`.
![[src/img/Pasted image 20240207163030.png]]

### 6. Crear un DHCP en un Router
#### **Nota: Asignar IPS Antes de TODO**
#### Pasos Básicos:
1. **Entrar al Modo de Configuración Global:**
2. **Activar el Servicio DHCP:**
    - Habilita el servicio DHCP en el router con el comando `service dhcp`.
3. **Crear un Pool de DHCP:**
    - Define un pool de DHCP utilizando el comando `ip dhcp pool [nombre_del_pool]`, donde `[nombre_del_pool]` es un identificador para el pool de direcciones IP que estás creando.
4. **Especificar el Rango de Direcciones IP:**
    - Configura el rango de direcciones IP que será asignado a los clientes DHCP con el comando `network [dirección_de_red] [máscara_de_subred]`. Este comando define la red y la máscara de subred disponibles para los clientes DHCP.
5. **Establecer el Router Predeterminado:**
    - Asigna el router predeterminado (puerta de enlace) para los clientes DHCP usando el comando `default-router [dirección_IP_del_router]`. Esto les dice a los clientes DHCP cuál es su puerta de enlace predeterminada.
    - 
1. **Excluir Direcciones IP:**
    - Para evitar conflictos de direcciones IP, puedes excluir direcciones IP específicas dentro del rango configurado con el comando `ip dhcp excluded-address [primera_dirección_IP] [última_dirección_IP]`. Esto es útil para direcciones IP que están estáticamente asignadas y no deben ser entregadas por el DHCP.
	    ![[src/img/Pasted image 20240207170945.png]]
7. Comandos usados - (por si quereis copiar y pegar)
```
service dhcp - Usamos el servicio DHCP
ip dhcp pool andared - Creamos la POOL de IPS
network 192.168.90.0 255.255.255.0 - Especificamos la red de la POOL del DHCP

default-router 192.168.90.1 - Especificamos la puerta de enlace
ip dhcp excluded-address 192.168.90.127 192.168.90.254 - Indicamos al dhcp que no queremos que asigne esas ips


"Esto es para configurar un DHCP-DNS"
ip dhcp pool andared
dns-server 192.168.90.1
exit
```

8. **Resultado Final**
	![[src/img/Pasted image 20240207171144.png]]
#### Parámetros Opcionales:

**NOTA: Puede caer o no en el examen porque estos son parametros de un servidor dhcp, estas opciones se ven el segundo año del modulo mejor con mas tiempo y mejores herramientas.**

7. **Especificar Servidores DNS:**
    - Para que los clientes DHCP puedan resolver nombres de dominio, especifica la dirección IP de uno o más servidores DNS con `dns-server [dirección_IP_del_DNS]`. Puedes especificar múltiples servidores DNS separándolos con espacios.
8. **Establecer el Dominio Predeterminado:**
    - Define el dominio predeterminado que se asignará a los clientes DHCP con el comando `domain-name [nombre_del_dominio]`.
9. **Asignar una Dirección IP Específica:**
    - Para reservar una dirección IP para un dispositivo específico, usa el comando `ip dhcp pool [nombre_del_pool]` seguido de `host [dirección_IP_deseada] [máscara_de_subred]` y luego especifica la dirección MAC del dispositivo con `client-identifier [dirección_MAC]` o `hardware-address [dirección_MAC] ethernet`.
10. **Configurar el Tiempo de Asignación (Lease Time):**
    - Configura el tiempo de asignación de las direcciones IP con `lease [días] [horas] [minutos]`. Esto define cuánto tiempo un cliente puede mantener una dirección IP antes de que tenga que renovarla.

# 7. Enrutamiento

Los routers necesitan conocer cómo llegar a distintas redes que no están directamente conectadas a ellos para poder enviar y recibir tráfico hacia y desde esas redes.s

Para visualizar las rutas del router se usa este comado: show ip route
![[src/img/Pasted image 20240207212212.png]] (NOTA en este ejemplo del comando se usa rutas estaticas)
## Dinámico

Para facilitar la gestión del enrutamiento entre múltiples redes, se puede utilizar el protocolo de enrutamiento dinámico. En este ejemplo, usaremos RIP en su versión 2 para enrutar entre ocho redes diferentes:

- 172.16.0.0/16
- 172.17.0.0/16
- 172.18.0.0/16
- 172.19.0.0/16
- 172.20.0.0/16
- 172.21.0.0/16
- 172.22.0.0/16
- 172.23.0.0/16

Cada router tendrá una dirección IP dentro del bloque 10.0.0.0/8, que se utilizará para el enrutamiento entre ellos.

### Configuración de RIP versión 2

Para configurar RIP versión 2 en un router de cisco (Recordemos que packet tracer es de cisco) y facilitar el enrutamiento entre las redes anteriormente mencionadas, sigue los siguientes pasos:

1. Usa el comando `configure terminal` para entrar al modo de configuración.
2. **Habilitar RIP versión 2:**
   ```plaintext
   Router(config)# router rip
   Router(config-router)# version 2
   ```

3. **Anunciar Redes:**
   Anuncia cada red que el router debe conocer. Debes hacer esto para todas las redes directamente conectadas al router.
   ```plaintext
   Router(config-router)# network 172.16.0.0
   Router(config-router)# network 10.0.0.0

   ```
   Repite el comando `network "Direccion de red"` en cada uno de los routers 
   
Estos pasos se deben repetir en cada uno de los routers que participan en el enrutamiento, asegurándose de anunciar solo las redes directamente conectadas a cada router.

#### Resultado final de los comandos
he escogido el router con la red 172.16.0.0 como ejemplo de los comandos que hay que poner 
![[src/img/Pasted image 20240207204212.png]]

## Estático

El enrutamiento estático, a diferencia del dinámico, requiere que se configure manualmente cada ruta hacia las redes destino. Esto implica especificar explícitamente, en cada router, cómo alcanzar cada red no directamente conectada. A continuación, se describe cómo configurar enrutamiento estático para una red. (en la actualidad no se utiliza esto porque existen muchas redes y imaginate )

### Configuración de Enrutamiento Estático

1. **Entrar al Modo de Configuración Global:**
   - Usa el comando `configure terminal` para entrar al modo de configuración.

2. **Configurar una Ruta Estática:**
   - Para agregar una ruta estática, utiliza el comando `ip route`, seguido de la red destino, la máscara de subred, y el siguiente salto o interfaz de salida.
     ```plaintext
     Router(config)# ip route 172.16.0.0 255.255.0.0 10.0.0.2
     ```
   - Repite este paso para cada red destino, especificando el adecuado siguiente salto o interfaz de salida.

3. **Guardar la Configuración:**
   - Guarda la configuración al salir del modo de configuración y usar el comando `copy running-config startup-config`.
   Supongamos que quiero enrutar 8 router pues repetir todas estas tablas entre si:
   ![[src/img/Pasted image 20240207211745.png]]
   Resultado final:
   ![[src/img/Pasted image 20240207214404.png]]Los resquest timed out son porque tiene que hacer el protocolo ARP en las redes donde este el dispositivo conectado.

---
# Vlans - Switch/Router Edition

¿Que es una VLAN?

Una VLAN (Virtual Local Area Network) es un método que se utiliza para crear redes independiente (Capa 2 - Modelo OSI)  dentro de una misma red física (Capa 1 - Modelo OSI), permitiendo segmentar grupos de dispositivos aunque estén interconectados físicamente. Las VLANs se utiliza para crear varias redes dentro de un mismo.

**"Una VLAN SE CONSIDERA UNA INTERFAZ CONFIGURABLE"**
## Switch

### Cambiar de Vlan 1 a Vlan "numerito que se te antoje"

1. **Entrar al Modo de Configuración Global:**
   ```plaintext
   Switch> enable
   Switch# configure terminal
   ```

2. **Crear la VLAN:**
   Suponiendo que el "numerito que se te antoje" es 10, para crear la VLAN 10, ejecuta:
   ```plaintext
   Switch(config)# vlan 10
   Switch(config-vlan)# name Mi_VLAN
   ```

3. **Asignar Puertos a la VLAN:**
   Para asignar un puerto al switch a la VLAN 10, primero debes entrar a la configuración del puerto y luego asignarlo a la VLAN. Por ejemplo, para el puerto FastEthernet 0/1:
   ```plaintext
   Switch(config)# interface fastEthernet 0/1
   Switch(config-if)# switchport mode access - (Por defecto esto no hace falta pero no viene mal ponerlo )
   Switch(config-if)# switchport access vlan 10
   ```

Resultado Final 
![[src/img/Pasted image 20240209112446.png]]

Resultado Final - Alternativo
![[src/img/Pasted image 20240209112053.png]]
Nota: Si no existe la VLAN creada en el switch la crea 

### Truncar el Puerto del Switch

¿Que es un puerto trunk?
Un puerto trunk en una red de área local (LAN) es una interfaz de switch configurada para transportar tráfico de varias VLANs a través de un único enlace físico(Capa 1 - Fisica) entre dos dispositivos de red. (En router no hace falta truncarlo)

Para configurar un puerto como trunk (esto permite que el puerto transporte tráfico de múltiples VLANs), sigue estos pasos:

1. **Seleccionar el Puerto:**
   Accede a la configuración del puerto que deseas configurar como trunk. Por ejemplo, FastEthernet 0/24 - (Se usan los puertos mas bajos y incluso se puede usar los puertos gigabit del switch):
   ```plaintext
   Switch(config)# interface fastEthernet 0/24
   ```

2. **Configurar el Puerto como Trunk:**
   ```plaintext
   Switch(config-if)# switchport mode trunk
   ```

Resultado Final.
![[src/img/Pasted image 20240209122010.png]]
3. **Especificar VLANs Permitidas (opcional - No cae en examen pero lo coloco):**
   Puedes especificar qué VLANs están permitidas a través del trunk:
   ```plaintext
   Switch(config-if)# switchport trunk allowed vlan add 10
   ```
   Si omites este paso, el puerto permitirá todas las VLANs por defecto.

## Router

### Habilitar una VLAN en la Interfaz Concreta del Router

Para configurar subinterfaces en un router (permitiendo que una interfaz física maneje múltiples VLANs), sigue estos pasos:

1. **Entrar al Modo de Configuración Global:**
   ```plaintext
   Router> enable
   Router# configure terminal
   ```

2. **Crear Subinterfaces:**
   Por cada VLAN, crea una subinterfaz en la interfaz física del router. Supongamos que la interfaz es GigabitEthernet 0/0 y queremos configurar para la VLAN 10:
   ```plaintext
   Router(config)# interface GigabitEthernet 0/0.10
   Router(config-subif)# encapsulation dot1Q 10
   ```

Resultado Final
![[src/img/Pasted image 20240209123527.png]]
### Colocar IPs en Cada Una de las VLAN

Después de habilitar las VLANs en las subinterfaces, debes asignar una dirección IP a cada subinterfaz para permitir la comunicación entre las VLANs:

1. **Asignar Dirección IP:**
   Continuando con el ejemplo de la VLAN 10 en la subinterfaz GigabitEthernet 0/0.10:
   ```plaintext
   Router(config-subif)# ip address 192.168.10.1 255.255.255.0
   ```
   Repite este proceso para cada VLAN/subinterfaz, asegurándote de utilizar direcciones IP y máscaras de subred adecuadas para cada segmento de red.

Resultado Final
![[src/img/Pasted image 20240209123851.png]]
2. **Activar la Interfaz Física:**
   No olvides activar la interfaz física principal si aún no está activa:
   ```plaintext
   Router(config)# interface GigabitEthernet 0/0/0
   Router(config-if)# no shutdown
   ```






