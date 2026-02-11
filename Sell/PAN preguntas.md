- Perimetral o de segmentacion:
- Zonas a proteger y filtrar:
- Dispositivos aledaños(switches o routers):

- Ancho de banda:
- Cantidad de interfaces:
- Tuneles IPsec:
- Usuarios en red:
- Endpoints:


| User Question            | Your Input (B) | Calculation / Logic (C)                                                                               |
| ------------------------ | -------------- | ----------------------------------------------------------------------------------------------------- |
| Current Bandwidth (Gbps) |                | Base traffic entry.                                                                                   |
| Growth Factor (%)        |                | Future-proofing buffer.                                                                               |
| Headroom Safety (%)      | 70%            | Keeps CPU < 70%.                                                                                      |
| Role (Perimeter/Segment) |                | Defines whether the device focuses on deep threat inspection or high-speed internal routing.          |
| SSL Decryption? (Y/N)    |                | A resource-heavy process that significantly increases CPU load to inspect encrypted traffic.          |
| VPN Users (GP)           |                | The maximum number of simultaneous remote access tunnels the hardware must maintain.                  |
| Direct Connections       |                | The count of physical copper or fiber ports required to connect your infrastructure.                  |
| vsys Needed? (Y/N)       |                | The requirement for logical partitioning to manage multiple distinct networks on one physical device. |
