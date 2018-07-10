# ZBX-INFINERA-XTM-SERIES-MONITORING

## Optical Amplifiers
NOTE: Testing good with OA-RAED-21HG HYB and OA-20C-LG

- Discovery: XTM Series::Optical Amplifiers

    - XTM Series | OA interface $1
    - XTM Series | OA Operational State for the interface  $1
    - XTM Series | OA Adminintrative State for the interface  $1
    - XTM Series | OA Rx power level on $1
    - XTM Series | OA Tx power level on $1

- Triggers:

    - oaIfLossOfSignal                [5.160] Loss of Signal

me@zabbix:~$ snmptranslate -m /usr/share/snmp/mibs/LUM-OA-MIB.txt -Td -Ib 'oaIfLossOfSignal' | grep "SYNTAX\|DESCR"
  SYNTAX	INTEGER {ok(1), alarm(2)}
  DESCRIPTION	"Loss of signal.
me@zabbix:~$

    - oaIfReceivedPowerLow            [5.166] Low Received Optical Power
    - oaIfLaserBiasHigh               [5.106] High Laser Bias
    - oaIfPumpLaserTempLow            [5.224] Pump Laser Temp Low
    - oaIfSaturationFault             [5.8]   Amplifier Saturation alarm
    - oaIfOutputPowerFail             [5.203] Output power failed
    

## License
This template is distributed under the terms of the GNU General Public License as published by the Free Software Foundation

## Copyright
Copyright (c) Bruno Filipe Teixeira
