# Repositorio Oficial de Prácticas en Cisco Packet Tracer — *Redes Cisco desde Cero hasta CCNA*

Este repositorio público acompaña al manual técnico **Redes Cisco desde Cero hasta CCNA: Manual Práctico de Taller, Packet Tracer y Preparación PTSA** (**Francisco Sánchez Ruz**, Editorial Monsálvez).

- **Descarga rápida en 1 clic:** En la sección [**Releases**](https://github.com/franciscosanchezruz/redes-cisco-ccna/releases) puedes descargar el paquete completo **`Labs_Packet_Tracer_CCNA.zip`** con las **14 topologías `.pkt`** organizadas por bloques.
- **Compatibilidad:** Todos los archivos `.pkt` han sido creados y verificados en **Cisco Packet Tracer 8.2.1** (compatibles con versiones `8.2.1` o superiores).

---

## 1. Estructura de Prácticas Guiadas (`_inicio.pkt` + `_solucion.pkt`)

Cada práctica de taller incluye dos archivos:
- `*_inicio.pkt`: topología base lista para realizar la configuración paso a paso desde cero.
- `*_solucion.pkt`: práctica completamente configurada y verificada para contrastar resultados.

| Bloque | Archivos `.pkt` | Qué se practica | Comandos clave de verificación |
| :--- | :--- | :--- | :--- |
| **00. Taller desde Cero** | `00_taller_desde_cero/practica_01_taller_basico_inicio.pkt`<br>`00_taller_desde_cero/practica_01_taller_basico_solucion.pkt` | Cableado Ethernet, Switch 2960 + 2 PCs, asignación IPv4 y prueba `ping`. | `ipconfig`<br>`ping 192.168.10.11` |
| **01. CCNA 1 (ITN)** | `01_ccna1_itn/practica_02_itn_sede_central_inicio.pkt`<br>`01_ccna1_itn/practica_02_itn_sede_central_solucion.pkt` | Router `R-SedeCentral` (`2911`) + 2 Switches (`2960`) + 3 PCs + Servidor. Doble VLSM `172.16.20.0/24` (`/27` + `/28`), IPv6 Dual-Stack `FE80::1`, SVI en `SW-Planta2` y SSHv2. | `show ip interface brief`<br>`show ipv6 interface brief`<br>`ping 172.16.20.1` |
| **02. CCNA 2 (SRWE)** | `02_ccna2_srwe/practica_03_srwe_etherchannel_vlans_inicio.pkt`<br>`02_ccna2_srwe/practica_03_srwe_etherchannel_vlans_solucion.pkt` | VLANs (`10 DOCENCIA`, `20 GESTION`, `99 NATIVA`, `999 PARKING`), **EtherChannel LACP activo (`Po1(SU)`)** y Trunk 802.1Q (`nonegotiate`). | `show etherchannel summary`<br>`show vlan brief`<br>`show interfaces trunk` |
| **03. CCNA 3 (ENSA)** | `03_ccna3_ensa/practica_04_ensa_ospf_acl_nat_inicio.pkt`<br>`03_ccna3_ensa/practica_04_ensa_ospf_acl_nat_solucion.pkt` | **OSPFv2** (`router ospf 1`, `router-id 1.1.1.1`, `area 0`, `passive-interface g0/1`), ACL extendida `ACL_FILTRO_AULA`, ACL estándar `10` y **PAT/NAT Overload** hacia WAN `203.0.113.0/30`. | `show ip protocols`<br>`show ip ospf interface brief`<br>`show access-lists`<br>`show ip nat translations` |
| **04. Clínica de Averías** | `04_clinica_averias/practica_05_averia_vlan_trunk_inicio.pkt`<br>`04_clinica_averias/practica_05_averia_vlan_trunk_solucion.pkt` | Escenario con averías intencionadas en `SW-Clinica-Averias` y `Router0` para entrenar el diagnóstico sistemático en 5 minutos. | `show interfaces status`<br>`show vlan brief`<br>`ping 192.168.10.1` |

---

## 2. Simulacros Completos de Examen Práctico (PTSA)

Plantillas `.pkt` base preparadas en Cisco Packet Tracer 8.2.1+ para entrenar los 4 simulacros integradores del libro:

| Archivo | Simulacro | Capítulo de referencia |
| :--- | :--- | :---: |
| `05_simulacros_ptsa/simulacro_01_ptsa_itn_inicio.pkt` | Simulacro PTSA CCNA 1 (ITN): Doble VLSM + IPv6 Dual-Stack | Capítulo 3 |
| `05_simulacros_ptsa/simulacro_02_ptsa_srwe1_inicio.pkt` | Simulacro PTSA CCNA 2 (SRWE P1): VLANs, Trunk 802.1Q, LACP y MLS | Capítulo 6 |
| `05_simulacros_ptsa/simulacro_03_ptsa_srwe2_inicio.pkt` | Simulacro PTSA CCNA 2 (SRWE P2): Seguridad L2, WLC-2504 y RADIUS | Capítulo 8 |
| `05_simulacros_ptsa/simulacro_04_ptsa_ensa_inicio.pkt` | Simulacro PTSA CCNA 3 (ENSA): OSPFv2 Área 0, ACLs, PAT y NTP/Syslog | Capítulo 12 |

---

## 3. Credenciales de Laboratorio en Archivos `*_solucion.pkt`

| Función / Modo | Usuario | Contraseña en el Libro / `.pkt` | Comando Asociado |
| :--- | :---: | :---: | :--- |
| **Modo Privilegiado (`enable`)** | N/A | `AdminSede2026!` / `CiscoEnable2026!` | `enable secret AdminSede2026!` |
| **Consola Física (`line con 0`)** | N/A | `CiscoConsola2026!` | `password CiscoConsola2026!` + `login` |
| **Acceso Remoto SSHv2 (`line vty`)** | `admin` | `SSHSede2026!` / `AdminSSH2026!` | `username admin secret SSHSede2026!` |
| **Redes Wi-Fi WPA2-PSK (WLC)** | SSID Alumnos / Profes | `AlumnosAdmin2026!` / `DocentesAdmin2026!` | WPA2 Policy (AES) + PSK |

---

## Aviso Legal, NDA y Marcas Registradas

Todos los archivos `.pkt` de este repositorio son **creaciones originales** desarrolladas con fines didácticos conforme al **Art. 32.1 del TRLPI**, sin reproducir enunciados ni preguntas confidenciales de exámenes oficiales. *Cisco*, *CCNA* y *Packet Tracer* son marcas registradas de Cisco Systems, Inc. (uso descriptivo nominativo, Art. 37.1.c Ley 17/2001, de Marcas).
