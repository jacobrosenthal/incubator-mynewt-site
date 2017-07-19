
## GAP API for bletiny

<br>

Generic Access Profile (GAP) defines the generic procedures related to discovery of Bluetooth devices (idle mode procedures) and link management aspects of connecting to Bluetooth devices (connecting mode procedures). It also defines procedures related to use of different security levels. 

Several different modes and procedures may be performed simultaneously over an LE physical transport. The following modes and procedures are defined for use over an LE physical transport:

1. **Broadcast mode and observation procedure**
    - These allow two devices to communicate in a unidirectional connectionless manner using the advertising events.
2. **Discovery modes and procedures**
    - All devices shall be in either non-discoverable mode or one of the discoverable modes.
    - A device in the discoverable mode shall be in either the general discoverable mode or the limited discoverable mode.
    - A device in non-discoverable mode will not be discovered by any device that is performing either the general discovery procedure or the limited discovery procedure.
3. **Connection modes and procedures**
    - allow a device to establish a connection to another device.
    - allow updating of parameters of the connection 
    - allow termination of the connection
4. **Bonding modes and procedures**
    - Bonding allows two connected devices to exchange and store security and identity information to create a trusted relationship. 
    - Bonding can occur only between two devices in bondable mode.


<br>


### Usage API


|**Item No.** | **Modes and Procedures** | **nimBLE command** |
|----|---------|---------------|
|  1 | Broadcast Mode | `b adv conn=non disc=x` |
|    | Observation Procedure | `b scan dur=x disc=x type=x filt=x`  |
|  2 | Non-Discoverable mode   | `b adv conn=x disc=non`  |
|    | Limited Discoverable mode   | `b adv conn=x disc=ltd`  |
|    | General Discoverable mode   | `b adv conn=x disc=gen`  |
|    | Limited Discovery procedure | `b scan dur=x disc=ltd type=active filt=no_wl`  |
|    | General Discovery procedure | `b scan dur=x disc=gen type=active filt=no_wl`  |
|    | Name Discovery procedure  | `b scan dur=x` <br> `b scan cancel` <br> `b conn peer_addr_type=x peer_addr=x` <br> `b read uuid=0x2a00` |
|  3 | Non-connectable mode   | `b adv conn=non disc=x`  |
|   |  Directed connectable mode  | `b adv conn=dir disc=x addr_type=x addr=x`  |
|   |  Undirected connectable mode  | `b adv conn=und disc=x`  |
|   | Auto connection establishment procedure   | `b wl addr_type=x addr=x`  |
|   | Auto connection establishment procedure   | `b conn addr_type=wl`  |
|   |  General connection establishment procedure  | AVAILABLE SOON  |
|   | Selective connection establishment procedure   | AVAILABLE SOON  |
|   | Direct connection establishment procedure  | `b conn addr_type=x addr=x [params]`  |
|   | Connection parameter update procedure   | `b update conn=x <params>`  |
|   |  Terminate connection procedure  | `b term conn=x`  |
|  4 |   Non-Bondable mode | AVAILABLE SOON |
|   | Bondable mode   | AVAILABLE SOON |
|   | Bonding procedure   | AVAILABLE SOON |

<br>
### Connection Parameters 

The Connection parameter definitions can be found in Section 7.8.12 of the BLUETOOTH SPECIFICATION Version 4.2 [Vol 2, Part E].

|**Name** | **Description** | **nimBLE parameter** |
|----|---------|---------------|
| Minimum connection interval | Defines minimum allowed connection interval| itvl_min  |
| Maximum connection interval | Defines maximum allowed connection interval |  itvl_max |
| Conn_Latency | Defines the maximum allowed connection latency | latency |
| Supervision_Timeout | Link supervision timeout for the connection. | timeout |
|LE_Scan_Interval  | Recommendation from the Host on how long the Controller should scan | scan_itvl  |
|LE_Scan_Window  |Recommendation from the Host on how frequently the Controller should scan | scan_window |
|Minimum_CE_Length  | Informative parameter providing the Controller with the expected minimum length of the connection event|  min_ce_len |
|Maximum_CE_Length |Informative parameter providing the Controller with the expected maximum length of the connection event  | max_ce_len |

### Advertisement data fields

