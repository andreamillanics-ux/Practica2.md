# Modelado de Amenazas: Sistema de Autenticación y API de Usuarios

**Fecha:** 2026-08-31  
**Versión:** 1.1 (Corregido)  
**Autores:** [Andrea Marely Millan Elias / 4°A]

## 1. Diagrama de Flujo de Datos (DFD) con Mermaid.js

```mermaid
graph TD
    classDef internet fill:#f9f,stroke:#333,stroke-width:2px,color:#000000;
    classDef secureZone fill:#bbf,stroke:#333,stroke-width:2px,color:#000000;

    Usuario["🌐 Usuario (Navegador/App)"] -->|"1. Envía Credenciales (HTTPS)"| API["⚙️ API Gateway / Backend"]
    Admin["🧑‍💼 Administrador de Red"] -->|"5. Mantenimiento (SSH)"| BD[("💾 Base de Datos SQL")]

    API -->|"2. Consulta / Guarda Usuario"| BD
    API -->|"3. Valida Token"| Auth["🔑 Servicio de Auth Externo (OAuth)"]

    subgraph "Frontera de Internet (Insegura)"
        Usuario
    end

    subgraph "Red Interna de la Empresa (Zona Segura)"
        API
        BD
        Auth
    end

    class Usuario internet;
    class API,BD,Auth secureZone;
