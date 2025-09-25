Laboratorio 2 Implementación de Rutas Estáticas y RIPv2

Objetivos especificos
-Configurar y verificar rutas estáticas para lograr conectividad en una red multi-router.
-Implementar el protocolo de enrutamiento dinámico RIPv2 para anunciar y aprender rutas automáticamente.
-Analizar y comparar los resultados en la tabla de enrutamiento de ambos métodos.
-Verificar la conectividad de extremo a extremo con ping y traceroute.

Se construirá una topología de tres routers, donde cada router conecta una LAN independiente.

Dispositivos: 3 Routers (modelo 4321), 3 Switches (modelo 2960), 3 PCs.
Conexiones WAN: Se utilizarán conexiones seriales entre los routers. añadiremos los módulos seriales a los routers antes de conectarlos.
R1 (Se0/0/0) <--> R2 (Se0/0/0)
R2 (Se0/0/1) <--> R3 (Se0/0/1)
Conexiones LAN: Cada router se conecta a su respectivo switch (G0/0/0 a G0/1) y cada switch a su PC (F0/1 a F0).

TABLA DE DIRECCIONAMIENTO<P>
![image_Alt](https://github.com/NETD3VIL/Practicas_CiscoPacketTracer/blob/3824f9912f1cb16c1c381862253d27b3810cc7c2/tabla_rutas_Lab1.png)<p><p>
Utilizamos los siguientes comandos para realizar el enrutamiento en cada router solo sustituimos las ip conforme a la tabla de direccionamiento<p>
```
R1(config)# ip route 192.168.2.0 255.255.255.0 10.1.1.2
```
```
R1(config)# ip route 192.168.3.0 255.255.255.0 10.1.1.2
```
<p>
En R3 configuramos las rutas estáticas para alcanzar LAN de R1 y R2 apuntando a la IP del siguiente salto en R2.<p>
En R2 configuramos las rutas estáticas para alcanzar LAN de R1 y R3, apuntando a las IPs de siguiente salto correspondientes.<p>

Verificación:
En la siguiente imagen podemos observar la topologia de la red y un ping exitoso de PC1 a PC2 utilizando de enrutamiento estático 
<p>

![image_Alt](https://github.com/NETD3VIL/Practicas_CiscoPacketTracer/blob/dc4f06460201eff124cebec6756c5aad54848ab0/topologia_ping1.png)<p><p>
<p><p>
Utilizando el comando show ip route con enrutamiento estatico<p>
  
![image_Alt](https://github.com/NETD3VIL/Practicas_CiscoPacketTracer/blob/7664d52ea79bb2abcb3aeea0a6995b0b2e3a0f84/ip_route_estatico.png)<p>



