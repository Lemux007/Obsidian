**SLIDE 1 — PORTADA**

- El Shadow AI clásico (usuario abriendo ChatGPT) ya es el problema de ayer
- El problema de 2026 son los agentes autónomos + MCP corriendo sin supervisión de TI
- Tres fabricantes, tres filosofías arquitectónicas distintas — eso es lo que vamos a diseccionar hoy

---

**SLIDE 2 — EL PUNTO CIEGO DEL SOC**

- **Inventario:** nadie sabe cuántas instancias de Claude, Copilot o GPT están activas en la red hoy — ni cuántos tokens corporativos están expuestos
- **Tráfico:** viaja sobre TLS estándar, HTTP/2 o HTTP/3 — idéntico a cualquier navegación web segura, sin firma de malware que lo distinga
- **SIEM:** clasifica todo como tráfico legítimo → cero alertas → el dashboard está en verde mientras la exfiltración ocurre
- Pregunta para abrir debate: ¿cuántos de ustedes tienen visibilidad de qué modelos de IA están siendo consultados desde su red hoy?

---

**SLIDE 3 — EL RIESGO**

- **Exfiltración:** no es un malware, es una API call legítima que lleva código fuente, PII o credenciales hacia afuera
- **IPI:** el agente lee un documento o correo con instrucciones ocultas en lenguaje natural → las ejecuta sin saberlo → no hay payload malicioso que detectar
- **ZombieAgent:** una vez alterada la memoria a largo plazo del agente, el atacante tiene un insider con credenciales legítimas que opera indefinidamente
- Punto clave: el vector de ataque ya no es el código — es el lenguaje natural dentro de los datos

---

**SLIDE 4 — PALO ALTO**

- Su apuesta: controlar en tránsito de red, antes de que el paquete llegue al destino
- Rompen el cifrado TLS de forma controlada → inspeccionan el payload en texto plano → construyen una firma del agente ("Agentic Identity")
- Si la firma viola políticas → TCP RST inmediato, sesión terminada
- Fortaleza: un solo punto de gobierno para toda la organización
- Ideal para entornos con Prisma SASE o NGFW ya desplegados — la integración es nativa

---

**SLIDE 5 — TREND MICRO**

- Su apuesta: el control no está en la red, está dentro del kernel del endpoint
- El driver XDR intercepta la llamada de sistema antes de que salga del equipo — captura proceso padre, proceso hijo, hash, memoria
- Todo cruza con la identidad del usuario vía ZTSA → el contexto es completo: quién, desde qué app, con qué dispositivo
- Fortaleza: saben exactamente que fue VS Code → node.js → plugin no autorizado, no solo "hubo tráfico a OpenAI"
- Ideal cuando necesitan atribuir el incidente a un proceso y un usuario específico

---

**SLIDE 6 — RADWARE**

- Su apuesta: proteger el lado del servidor, sin tocar endpoints ni red interna
- El Risk Graph Map muestra en tiempo real las dependencias entre agentes y APIs — el problema se ve antes de que explote
- EPIC-AI analiza comportamiento puro: RPS, patrones JSON, firma del cliente HTTP → detecta headless browsers agénticos mutando cabeceras
- Respuesta: reto criptográfico o invalidación de token → sin necesidad de firmas estáticas ni actualizaciones de reglas
- Ideal para arquitecturas cloud-native o microservicios donde instalar agentes en cada endpoint no es viable

---

**SLIDE 7 — CONCLUSIÓN**

- Ninguno de los tres es "el mejor" — cada uno ganó en su propio dominio
- **Palo Alto** → gobierno perimetral centralizado
- **Trend Micro** → contexto profundo del host y del usuario
- **Radware** → protección del lado servidor sin fricción en endpoints
- Los tres entregan lo mismo al negocio: visibilidad total, contención automatizada, base auditable para reguladores
- Cierre: la oportunidad es pasar de ser el equipo que dice "no" a ser el habilitador que hace que la adopción de IA sea sostenible


