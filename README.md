# PulsoPC

Diagnóstico, preparación y pruebas de estrés para PCs recién ensambladas, con reporte para el cliente. Corre desde una USB con el PowerShell 5.1 que trae Windows 10/11: no hay que instalar nada en el equipo.

![PowerShell](https://img.shields.io/badge/PowerShell_5.1-5391FE?style=flat-square&logo=data:image/svg%2bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0ibm9uZSIgc3Ryb2tlPSJ3aGl0ZSIgc3Ryb2tlLXdpZHRoPSIyLjUiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIgc3Ryb2tlLWxpbmVqb2luPSJyb3VuZCIgZD0iTTQgNmw3IDYtNyA2TTEzIDE4aDciLz48L3N2Zz4=&logoColor=white) ![Windows](https://img.shields.io/badge/Windows_10_|_11-0078D6?style=flat-square) ![Pester](https://img.shields.io/badge/Pester_·_367_pruebas-3E8A5A?style=flat-square&logo=data:image/svg%2bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0ibm9uZSIgc3Ryb2tlPSJ3aGl0ZSIgc3Ryb2tlLXdpZHRoPSIzIiBzdHJva2UtbGluZWNhcD0icm91bmQiIHN0cm9rZS1saW5lam9pbj0icm91bmQiIGQ9Ik00IDEyLjVsNSA1TDIwIDYuNSIvPjwvc3ZnPg==&logoColor=white)

> 🔒 **Código privado.** Este repositorio muestra el proyecto; el código está disponible a pedido en oropeza.dev@gmail.com.

## Lo más destacado

- **Sin instalar nada:** corre desde una USB con lo que ya trae Windows (PowerShell 5.1 y .NET), incluso en equipos recién formateados o sin internet.
- **Tres servicios de taller:** puesta a punto de PCs nuevas, diagnóstico con ficha de recepción y reparación con mediciones antes y después.
- **Diagnóstico profundo:** salud SMART de discos, temperaturas y ventiladores, pantallazos azules explicados, caídas del driver de video, red capa por capa, impresoras, Windows Update, amenazas y programas que se cierran.
- **Pruebas de estrés** de CPU, RAM, disco y GPU (WebGL propio), con un registro de seguridad que se guarda aunque el equipo se reinicie.
- **Atención remota segura:** paquete cifrado con AES-256, código de un solo uso, vencimiento y autolimpieza.
- **Dos reportes por servicio:** uno para el cliente, claro y sin jerga (HTML, PDF y resumen para WhatsApp), y un informe técnico completo para el taller.
- **Interfaz gráfica WPF** con avance visible y cancelación, además de los menús de consola, y **modo simulación** para probar sin tocar el equipo.

## Arquitectura

```mermaid
flowchart LR
    M[Menús .cmd] --> MENU[menu.ps1<br/>consola]
    M --> GUI[gui.ps1<br/>WPF]
    MENU --> KIT[kit.ps1<br/>orquestador]
    GUI -->|canal de archivos:<br/>avance, preguntas, cancelar| KIT
    KIT --> MOD[25 módulos .psm1<br/>Inventario, Diagnóstico, Estrés,<br/>Reparación, Red, Smart, Remoto…]
    MOD --> EXT[Herramientas externas<br/>LibreHardwareMonitor, smartctl,<br/>BlueScreenView, winget]
    MOD --> REP[Reporte.psm1]
    REP --> C[Reporte del cliente<br/>HTML · PDF · WhatsApp]
    REP --> T[Informe técnico]
    REP --> J[(datos.json)]
```

La lógica vive en módulos independientes con pruebas Pester; `kit.ps1` arma cada servicio combinándolos, y la interfaz gráfica lo ejecuta en segundo plano comunicándose por archivos, de modo que una prueba larga nunca congela la ventana.

## Capturas

Reporte real de un servicio de reparación, con los datos del cliente reemplazados.

**Reporte para el cliente**

![Reporte para el cliente](capturas/reporte-cliente.png)

**Informe técnico para el taller**

![Informe técnico](capturas/informe-tecnico.png)

## Requisitos del equipo

- Windows 10 versión 1803 o posterior, o Windows 11 (PowerShell 5.1 y .NET Framework 4.7.2 vienen incluidos).
- Edge o Chrome para la prueba de GPU (WebGL 2).

## Contacto

📬 oropeza.dev@gmail.com · [LinkedIn](https://www.linkedin.com/in/jhonatan-oropeza) · [Perfil de GitHub](https://github.com/oropezadev-wq)
