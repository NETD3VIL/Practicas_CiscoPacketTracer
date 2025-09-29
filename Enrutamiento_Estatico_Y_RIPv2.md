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

Utilizando el comando show ip route con enrutamiento RIPv2<p>
  
![image_Alt](https://github.com/NETD3VIL/Practicas_CiscoPacketTracer/blob/bcd57e3451faa0a57bcb51de49ad51816dee2c67/ip_route_RIPv2.png)<p>

Preguntas de análisis

Al ejecutar show ip route en R1 después de la Parte 2, ¿qué indica el código S y qué significa la notación [1/0]?
R=En la configuración estática S indica que dicho ruteo fue configurado de manera manual con ip route y la notación [0/1] es [Distancia administrativa/Métrica] donde la AD indica la confiabilidad de la ruta y entre más bajo el número la ruta es más confiable, en este caso es 1 por lo que quiere decir que es muy confiable y el otro parámetro que es “Métrica” indica que el costo fue 0 y de hecho en ruteos manuales con ip route siempre será 0 pero por ejemplo con RIP indica los hops o saltos entre cada router, con RIP se supone que debe alcanzar su objetivo por la ruta de menor costo (menos HOPS) por cuestiones de optimización o eficiencia.

Después de configurar RIPv2 en la Parte 3, ¿qué código de letra identifica las rutas aprendidas dinámicamente? ¿Qué significa la métrica (el segundo número en [120/X]) para una ruta RIP?
R= La letra que identifica las rutas aprendidas es R y la Métrica lo que indica son los HOPS o saltos entre routers en este caso si ejecutamos show ip route desde el router R1 indica que para llegar al router R2 solo realiza 1 salto y para llegar al R3 realiza 2 saltos porque tiene que pasar primero por R2.

Compara la configuración manual de la Parte 2 con la automática de la Parte 3. ¿Qué método consideras más escalable (fácil de administrar si se añaden más redes) y por qué?
R=El ruteo manual con ip route definitivamente no debe utilizarse en redes grandes porque una persona tardaría mucho realizando la configuración en cada router y no es para nada escalable, sin embargo RIPv2 en cuestión de minutos puedes implementarlo solo con unos cuantos comandos y los routers se encargan de dar a conocer sus networks, creo que la mayor ventaja es que con RIPv2 sería que puedes modificar la red sin realizar cambios en el ruteo y con ip route si tendrias que hacer cambios si agregas o retiras routers.

Conclusión
Fue muy interesante esta práctica ya que nos hace conocer las formas manuales y las formas más eficientes para realizar una conexión correcta entre routers, con RIPv2 bajamos considerablemente el nivel de errores humanos que se podrían cometer al hacerlo de manera manual, disminuimos el tiempo de configuración y también si existen modificaciones en la red de routers conectados RIPv2 ajusta la red y  no se pierde la comunicación mientras exista la conexión física entre ellos. Las múltiples ventajas que tiene RIPv2 es que tiene también un método de autenticación simple y siempre busca las rutas más óptimas (menos HOPS) para llevar a cabo la transmisión de datos.




