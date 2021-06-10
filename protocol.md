# Communication protocol

Thanks to ***bojer*** from trionictunning.com forum for initial information which fueled further reverse engineering.  

## Physical connection
SID is wired to ICM module and 115200baud UART over CAN physical layer is used. Most common MCP2551 CAN tranceiver connected to USB-to-serial adapter could serve for sniffing or development.  

## Communication sequence

SID act as slave device and always respond to ICM commands either with positive or negative respone. Command are sent in frames structured as below.  

### Frame format

| DLC(1) | PAYLOAD(N) | CHECKSUM(1) |
| --- | --- | --- |

DLC - length of payload  
PAYLOAD - actual command/response  
CHECKSUM - LSB of all payload bytes sum