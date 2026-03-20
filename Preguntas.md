## 1. Quick Reference & Explanations

## 1.1 & 1.2: Security in Workstations and Servers

- **What it is:** The "body armor" for individual computers and the central brains (servers) of the company.
    
- **How to explain if they don't know:** "If a virus tries to enter a single laptop or the main server, what is the first line of defense that stops it? We need to know if you have more than just a basic antivirus."
    
- **Key Terms:** * **EDR (Endpoint Detection & Response):** Like a security camera for the PC that records behavior to catch new threats.
    
    - **Host IPS:** A system that blocks suspicious "actions" rather than just looking for known "files."
        

## 1.3: Data Security & Content Control

- **What it is:** Tools that prevent sensitive info (credit cards, passwords, client lists) from leaving the company.
    
- **How to explain:** "How do you stop an employee or a hacker from accidentally or intentionally emailing your entire client database to a personal Gmail account?"
    
- **Key Term:** * **DLP (Data Loss Prevention):** Software that recognizes sensitive patterns (like ID numbers) and blocks them from being copied or sent.
    

## 1.4 & 1.5: System & Network Security

- **What it is:** The "walls and gates" of the digital office.
    
- **How to explain:** "The Firewall is your front door. The WAF is a special guard specifically for your website. Vulnerability Management is like checking all your windows regularly to see if the locks are broken."
    
- **Key Term:** * **SIEM:** A central dashboard that collects logs from everywhere to alert you if something looks like a coordinated attack.
    

## 1.6: Identity & Access Management (IAM)

- **What it is:** Proving people are who they say they are.
    
- **How to explain:** "Beyond a password, how do you verify a user? Do they get a code on their phone (MFA)? Is there a master list of employees (Active Directory)?"
    

---

## 2. Handling "I Don't Know" (The Approximation Strategy)

When a client doesn't have a specific number for **% Cobertura (Coverage)** or **How Many**, use these "Approximation Approaches" in Spanish.

## If they don't know "% Cobertura":

Ask for a **General Sentiment** or **Deployment Scope**.

- **Approach:** "¿Está instalado en todas las computadoras de la oficina, o solo en algunas áreas (como finanzas)?"
    
- **Calculation:**
    
    - "Todas": 95-100%
        
    - "La gran mayoría": 80-90%
        
    - "Solo los críticos/servidores": <50%
        
    - "Estamos en proceso de instalación": % actual instalado.
        

## If they don't know "How Much/Many":

Shift to **Infrastructure Brackets**.

- **Approach:** "Si no tiene el dato exacto, ¿podemos estimar por rangos? ¿Estamos hablando de menos de 100 usuarios, entre 100 y 500, o más de 1000?"
    
- **Spanish Phrase:** _"No se preocupe por el dato exacto ahorita. ¿Podemos trabajar con un orden de magnitud? ¿Es una implementación global o por departamentos?"_
    

## If they don't know "Vencimiento" (Expiration):

- **Approach:** "¿Sabe si la licencia se renovó este año o si es un contrato plurianual (3 años)?"
    
- **Spanish Phrase:** _"¿Recuerda cuándo fue la última vez que se gestionó el pago de estas licencias? Eso nos ayuda a estimar la vigencia."_
    

---

## 3. Dealing with "I don't know if I have it"

If they are unsure if a tool (like an EDR or WAF) exists:

- **Ask for the Brand:** "¿Tienen contratado algún servicio con Cisco, Fortinet, Crowdstrike o Microsoft?" (Often they know the brand but not the specific module).
    
- **Ask for the Pain Point:** "¿Qué pasa si alguien intenta entrar a su página web para tirarla? ¿Tienen algún servicio que proteja específicamente el sitio?"
    

---

## 4. Compliance & Plans (Section 2)

- **National/International:** Ask if they handle credit cards (PCI), health data (HIPAA/Local Law), or if they trade internationally (ISO 27001).
    
- **Operational Plans:**
    
    - **Incident Response:** "If you get hacked today, who is the first person you call and what is the first step?" (If they have no written answer, the answer is "No").
        
    - **DRP/BCP:** "If your server room burns down, how long does it take for the business to start selling/working again?"
      

