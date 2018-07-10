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
    
            me@zabbix:~$ snmptranslate -m /usr/share/snmp/mibs/LUM-OA-MIB.txt -Td -Ib 'oaIfReceivedPowerLow' | grep "SYNTAX\|DESCR"
            SYNTAX	INTEGER {ok(1), alarm(2)}
            DESCRIPTION	"Received power level low threshold exceeded.
            me@zabbix:~$
    
    - oaIfLaserBiasHigh               [5.106] High Laser Bias
    
            me@zabbix:~$ snmptranslate -m /usr/share/snmp/mibs/LUM-OA-MIB.txt -Td -Ib 'oaIfLaserBiasHigh' | grep "SYNTAX\|DESCR"
            SYNTAX	INTEGER {ok(1), alarm(2)}
            DESCRIPTION	"Laser bias high threshold exceeded.
            me@zabbix:~$
    
    - oaIfPumpLaserTempLow            [5.224] Pump Laser Temp Low
    
            me@zabbix:~$ snmptranslate -m /usr/share/snmp/mibs/LUM-OA-MIB.txt -Td -Ib 'oaIfPumpLaserTempLow' | grep "SYNTAX\|DESCR"
            SYNTAX	INTEGER {ok(1), alarm(2)}
            DESCRIPTION	"Pump laser temperature too low.
            me@zabbix:~$
    
    - oaIfSaturationFault             [5.8]   Amplifier Saturation alarm
    
            me@zabbix:~$ snmptranslate -m /usr/share/snmp/mibs/LUM-OA-MIB.txt -Td -Ib 'oaIfSaturationFault' | grep "SYNT\|DESCR\|Gain\|attr"
            SYNTAX	INTEGER {ok(1), alarm(2)}
            DESCRIPTION	"Saturation alarm threshold is passed. Actual Gain < (Wanted
            Gain -1 dB). The alarm can be cleared be cleared by reducing
            the wanted gain attribute.
            me@zabbix:~$
    
    - oaIfOutputPowerFail             [5.203] Output power failed
    
            me@zabbix:~$ snmptranslate -m /usr/share/snmp/mibs/LUM-OA-MIB.txt -Td -Ib 'oaIfOutputPowerFail' | grep "SYNT\|DESC\|Gain"
            SYNTAX	INTEGER {ok(1), alarm(2)}
            DESCRIPTION	"Output power failed alarm threshold is passed. Actual Gain < (Wanted
            Gain -1 dB) and Output Power < (Power Limit -1 dB).
            me@zabbix:~$
    
- Graph prototypes

![alt text](https://github.com/hacktivism-github/zbx-templates-repository/blob/master/images/Screen%20Shot%202018-07-10%20at%2021.54.05.png "Logo Title Text 1")
 
 

## License
This template is distributed under the terms of the GNU General Public License as published by the Free Software Foundation

## Copyright
Copyright (c) Bruno Filipe Teixeira
