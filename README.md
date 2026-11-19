# Repositorio de Prácticas y Modelos en Cisco Packet Tracer — *Redes Cisco desde Cero hasta CCNA (v1)*

Este repositorio acompaña al libro **Redes Cisco desde Cero hasta CCNA (v1): Manual Práctico de Taller, Packet Tracer y Preparación PTSA** (Francisco Sánchez Ruz, Editorial Monsálvez).

> **Compatibilidad:** Todos los archivos `.pkt` han sido creados y verificados en **Cisco Packet Tracer 8.2.1** (compatibles con versiones 8.2.1 o superiores).

---

## Estructura de Prácticas (`_inicio.pkt` + `_solucion.pkt`)

Cada práctica incluye dos archivos:
- `*_inicio.pkt`: topología base lista para que el alumnado realice la configuración desde cero.
- `*_solucion.pkt`: práctica completamente configurada y verificada para comprobar resultados.

| Bloque | Archivos `.pkt` | Qué practica el alumno | Comandos de autoevaluación |
| :--- | :--- | :--- | :--- |
| **00. Taller desde Cero** | `00_taller_desde_cero/practica_01_taller_basico_inicio.pkt`<br>`00_taller_desde_cero/practica_01_taller_basico_solucion.pkt` | Cableado Ethernet, Switch 2960 + 2 PCs, asignación IPv4 en Desktop y prueba `ping`. | `ipconfig`<br>`ping 192.168.10.11` |
| **01. CCNA 1 (ITN)** | `01_ccna1_itn/practica_02_itn_sede_central_inicio.pkt`<br>`01_ccna1_itn/practica_02_itn_sede_central_solucion.pkt` | Router `R-SedeCentral` (`2911`) + 2 Switches (`2960`) + 3 PCs + Servidor. Doble VLSM `172.16.20.0/24` (`/27` + `/28`), IPv6 Dual-Stack `FE80::1`, SVI en `SW-Planta2` y SSHv2. | `show ip interface brief`<br>`show ipv6 interface brief`<br>`ping 172.16.20.1` |
| **02. CCNA 2 (SRWE)** | `02_ccna2_srwe/practica_03_srwe_etherchannel_vlans_inicio.pkt`<br>`02_ccna2_srwe/practica_03_srwe_etherchannel_vlans_solucion.pkt` | VLANs (`10 DOCENCIA`, `20 GESTION`, `99 NATIVA`, `999 PARKING`), **EtherChannel LACP activo (`Po1(SU)`)** entre switches sin bloqueo STP y Trunk 802.1Q sin DTP (`nonegotiate`). | `show etherchannel summary`<br>`show vlan brief`<br>`show interfaces trunk` |
| **03. CCNA 3 (ENSA)** | `03_ccna3_ensa/practica_04_ensa_ospf_acl_nat_inicio.pkt`<br>`03_ccna3_ensa/practica_04_ensa_ospf_acl_nat_solucion.pkt` | **OSPFv2** (`router ospf 1`, `router-id 1.1.1.1`, `area 0`, `passive-interface g0/1`), ACL extendida `ACL_FILTRO_AULA`, ACL estándar `10` y **PAT/NAT Overload** hacia interfaz WAN `g0/0` (`203.0.113.1/30`) conectada a `Server0` (`203.0.113.2`). | `show ip protocols`<br>`show ip ospf interface brief`<br>`show access-lists`<br>`show ip nat translations` |
| **04. Clínica de Averías** | `04_clinica_averias/practica_05_averia_vlan_trunk_inicio.pkt`<br>`04_clinica_averias/practica_05_averia_vlan_trunk_solucion.pkt` | Escenario con fallo intencionado en `SW-Clinica-Averias` (`Fa0/1` apagada `disabled` y en `VLAN 1` en lugar de `VLAN 10 DOCENCIA`) conectado a `Router0` (`Fa0/3` trunk) para entrenar diagnóstico sistemático. | `show interfaces status`<br>`show vlan brief`<br>`ping 192.168.10.1` |

---

## Tabla Oficial de Credenciales de Laboratorio Utilizadas en las Prácticas

En caso de que un dispositivo de las soluciones (`*_solucion.pkt`) solicite autenticación en consola, modo privilegiado (`enable`) o sesión remota SSHv2:

| Función / Modo | Usuario | Contraseña en el Libro / `.pkt` | Comando de Configuración Asociado |
| :--- | :---: | :---: | :--- |
| **Modo Privilegiado (`enable`)** | N/A | `AdminSede2026!` / `CiscoEnable2026!` | `enable secret AdminSede2026!` |
| **Consola Física (`line con 0`)** | N/A | `CiscoConsola2026!` | `password CiscoConsola2026!` + `login` |
| **Acceso Remoto SSHv2 (`line vty`)** | `admin` | `SSHSede2026!` / `AdminSSH2026!` | `username admin secret SSHSede2026!` |
| **Redes Wi-Fi WPA2-PSK (WLC)** | SSID Alumnos / Profes | `AlumnosAdmin2026!` / `DocentesAdmin2026!` | WPA2 Policy (AES) + PSK |

---

## Guía Paso a Paso de Uso con el Libro

1. **Al comenzar cada bloque (Secciones 0 a 4):** Abre el archivo terminado en **`_inicio.pkt`** en Cisco Packet Tracer 8.2.1+.
2. **Aceleración de convergencia STP/OSPF/DHCP:** Tras conectar cables o encender puertos con `no shutdown`, pulsa **`Alt + D`** (*Fast Forward Time*) una o dos veces para adelantar 30 segundos el reloj de simulación y permitir que Spanning Tree pase de ámbar a verde.
3. **Comprobación autónoma:** Compara la salida de tus comandos `show` con las capturas reales del capítulo correspondiente y con el archivo **`_solucion.pkt`**.

---

## Aviso Legal, NDA y Marcas
Todos los archivos `.pkt` de este repositorio son **creaciones originales** desarrolladas para fines docentes al amparo del **Art. 32.1 del TRLPI**, sin copiar enunciados, topologías ni preguntas protegidas de terceros. *Cisco*, *CCNA* y *Packet Tracer* son marcas registradas de Cisco Systems, Inc., sin afiliación ni respaldo oficial.


## 05. Simulacros PTSA (Segunda Edición v2)

Plantillas `.pkt` base preparadas en Cisco Packet Tracer 8.2.1+ para los 4 simulacros prácticos del manual:

| Archivo | Simulacro | Capítulo |
|---|---|---|
| `05_simulacros_ptsa/simulacro_01_ptsa_itn_inicio.pkt` | Simulacro PTSA CCNA 1 (ITN) — Doble VLSM + IPv6 Dual-Stack | Capítulo 3 |
| `05_simulacros_ptsa/simulacro_02_ptsa_srwe1_inicio.pkt` | Simulacro PTSA CCNA 2 (SRWE P1) — VLANs, Trunk 802.1Q, LACP y MLS | Capítulo 6 |
| `05_simulacros_ptsa/simulacro_03_ptsa_srwe2_inicio.pkt` | Simulacro PTSA CCNA 2 (SRWE P2) — Seguridad L2, WLC-2504 y RADIUS | Capítulo 8 |
| `05_simulacros_ptsa/simulacro_04_ptsa_ensa_inicio.pkt` | Simulacro PTSA CCNA 3 (ENSA) — OSPFv2 Área 0, ACLs, PAT y NTP/Syslog | Capítulo 12 |
