# Communication protocol

Thanks to ***bojer*** from trionictunning.com forum for initial information which fueled further reverse engineering.  

## Physical connection
SID is connected to ICM module utilizing 115200 baud UART-based serial link over CAN physical layer (looks like same bus called [CGI](https://saabwisonline.com/d1/9-5/2011/3-electrical-system/bus-and-diagnostics-communication/technical-description-bus-and-diagnostics-communication/data-link-communications-description-and-operation/can-graphical-interface-cgi-circuit-description/) is used in SAAB 9-5NG cars ). Most common MCP2551 CAN tranceiver connected to USB-to-serial adapter could serve for sniffing or development.  

## Communication sequence

SID act as slave device and always respond to ICM commands either with positive or negative respone. Command are sent in frames structured as below.  

### Frame format

| DLC(1) | PAYLOAD(N) | CHECKSUM(1) |
| --- | --- | --- |

DLC - length of payload  
PAYLOAD - actual command/response  
CHECKSUM - LSB of all payload bytes sum