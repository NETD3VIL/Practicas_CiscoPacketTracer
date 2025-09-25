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
![image_Alt](https://github.com/NETD3VIL/Practicas_CiscoPacketTracer/blob/3824f9912f1cb16c1c381862253d27b3810cc7c2/tabla_rutas_Lab1.png)<p>

![image_Alt](https://github.com/NETD3VIL/Practicas_CiscoPacketTracer/blob/dc4f06460201eff124cebec6756c5aad54848ab0/topologia_ping1.png)<p>
En la imagen de arriba vemos la topologia de la red que consta principalmente de 3 routers conectados en serie y un ping exitoso en configuración de enrutamiento estático de PC1 a PC3
<p>
