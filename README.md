# 🛰️UCHAI 4 — Ground Station Dashboard

Este proyecto nace con la intención de recibir y decodificar señales satelitales del satelite SUCHAI4, esto en colaboración con
SPEAL, profesores y alumnos de la USACH y la Universidad de Chile.
Sumado a esto mostrar de forma interactiva el trabajo realizado a trabes de un Dashboard.

> **Feria Técnico Profesional de Programación 2026**  
> Proyecto interactivo de demostración de arquitectura web, propagación orbital y telemetría de satélites en órbita baja (LEO).

---

## Ficha Técnica de la Misión

| Parámetro | Especificación |
| :--- | :--- |
| **Formato** | 1U CubeSat ($10 \times 10 \times 10\text{ cm}$) |
| **Masa** | $\sim 1.3\text{ kg}$ |
| **Órbita** | LEO $\sim 500\text{ km}$ SSO (Inclinación: $97.5^\circ$) |
| **Período Orbital** | $\sim 95\text{ minutos}$ ($5700\text{ s}$) |
| **Velocidad Orbital** | $\sim 7.61\text{ km/s}$ |
| **Frecuencia Downlink** | UHF $437.225\text{ MHz}$ |
| **Protocolo de Enlace** | Tramas AX.25 (Radioaficionados / Ground Station) |
| **Estación Terrena Principal** | Santiago, Chile ($-33.45^\circ\text{ S}, -70.67^\circ\text{ W}$) |
| **Computador de Vuelo (OBC)** | MSP430 + Linux Embedded OBC |
| **Cargas Útiles (Payloads)** | Sonda Langmuir, Magnetómetro Triaxial |

---

## Características del Dashboard

*  **Rastreador Orbital 2D en Vivo:** Visualización cartográfica interactiva mediante [Leaflet.js](https://leafletjs.com/), con cálculo de traza sobre el terreno (ground track), huella de cobertura RF ($\sim 2500\text{ km}$) y marcador de estación terrena con indicador de enlace.
*  **Subsistema de Energía (EPS):** Monitorización de voltaje de paneles solares (ejes X, Y, Z), corriente generada y estado de carga de la batería Li-Ion.
*  **Telemetría Térmica y Cómputo (OBC):** Gráficos en tiempo real de temperaturas de CPU, placa base y payload, además de uso de CPU y memoria.
*  **Comunicaciones RF (COMMS):** Monitoreo de RSSI ($\text{dBm}$), relación señal-ruido (SNR en $\text{dB}$), tasa de datos y porcentaje de pérdida de paquetes.
*  **Terminal Decodificador AX.25:** Simulación de recepción de tramas en hexadecimal crudo y deserialización en tiempo real a objetos JSON.
*  **Panel de Demostración:** Conmutación entre modos operativos (*Nominal*, *Eclipse*, *Descarga de Payload*) y control de aceleración temporal (*Time Warp*).

---

## ️Arquitectura y Tecnologíass del Dashboard 

El proyecto está diseñado bajo un enfoque **Vanilla Web ligero y modular**, sin dependencias de compilación pesadas:

```
SuchaiWebTpToilet/
├── index.html                  # Estructura semántica del Centro de Control
├── css/
│   └── style.css               # Estilos HUD / Sistema de temas (Claro y Oscuro)
├── js/
│   ├── telemetry-simulator.js  # Motor de física y simulación de subsistemas
│   ├── orbit-tracker.js        # Motor de propagación orbital y Leaflet
│   ├── charts.js               # Gestor reactivo de gráficas Chart.js
│   ├── terminal.js             # Decodificador y formateador de tramas AX.25
│   └── app.js                  # Controlador principal y bucle de eventos
├── GUI_ROADMAP.txt             # Hoja de ruta y plan de rediseño técnico
└── README.md                   # Documentación oficial del proyecto
```

## Link de repositorios externos y guías de uso e instalación.
> https://spel.cl/news/2026/07/24/suchai4-decode.html 
  Quía de uso e instalación de las herramientas de decodificado.
> https://gitlab.com/scy-fi/thesis/diy-groundstation/-/blob/station_test/README.md?ref_type=heads
  Guía de uso e instalación de herramientas para grabar y captaar señales satelitales.
> https://gitlab.com/spel-uchile/suchai-4/suchai-4-groundstation
  Repositorios oficiales del trabajo realizado por SPEAL.

Ademas de las herramientas de sofware utlizadas en el proyecto cabe mencionar el uso de hardware utilizado
en el proyecto:

- Raspyberry 3
- Antena Yag
- Laptops personales

No fue requerido tanto material físico gracias a la versatilidad del software y las estaciones terrenas.
 
