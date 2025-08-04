El usuario desea agregar un correo pero no se aceptan las configuraciones que se proporcionan

### Con Telnet:

1. Abre la terminal (Windows: cmd con `telnet`, Linux/macOS: Terminal).
    
2. Usa:
    
    bash
    
    `telnet mail.tudominio.com 993`
    
    para verificar IMAP seguro, o
    
    bash
    
    `telnet mail.tudominio.com 143`
    
    para IMAP sin cifrar.  
    Si responde con `CONNECTED` u `220 ...`, significa que hay conexión [Server Fault+2freedomain.one+2Dropvps+2](https://freedomain.one/it-tools/email-tools/mx-check/?utm_source=chatgpt.com)[Reddit](https://www.reddit.com/r/verizon/comments/fcwckj?utm_source=chatgpt.com).
    
3. Para SMTP:
    
    bash
    
    `telnet mail.tudominio.com 587`
    
    o `465` (SSL) o `25`. De la misma forma, si responde con `220`, está activo.