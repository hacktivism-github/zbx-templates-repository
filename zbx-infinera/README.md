# ZBX-INFINERA-XTM-SERIES-MONITORING

## Equipment Status
Note: Testing good with both [TM-3000/II](https://www.infinera.com/wp-content/uploads/infinera-ds-tm-3000_ii-chassis.pdf) and 
[TM-301/II](https://www.infinera.com/wp-content/uploads/infinera-ds-tm-301_ii-chassis.pdf) Chassis

- Discovery: XTM Series::Equipment Status::Power Supply Status

    - XTM Series | equipmentPowerName $1
    - XTM Series | equipmentPowerType $1
    - XTM Series | equipmentPowerOperStatus $1
    - XTM Series | equipmentPowerDCPowerFailed $1
    - XTM Series | equipmentPowerDCPowerFailedSeverity $1
    
        - Triggers:

                me@zabbix:~$ snmptranslate -m /usr/share/snmp/mibs/LUM-EQUIPMENT-MIB.txt -Td -Ib 'equipmentPowerACPowerFailed' | grep "TEX\|SYNT\|DESC"
                -- TEXTUAL CONVENTION FaultStatus
                SYNTAX	INTEGER {ok(1), alarm(2)}
                DESCRIPTION	"AC power supply failed (230 V).
                me@zabbix:~$ snmptranslate -m /usr/share/snmp/mibs/LUM-EQUIPMENT-MIB.txt -Td -Ib 'equipmentPowerDCPowerFailed' | grep "TEX\|SYNT\|DESC"
                -- TEXTUAL CONVENTION AlarmPerceivedSeverity
                SYNTAX	INTEGER {undefined(0), cleared(1), indeterminate(2), warning(3), minor(4), major(5), critical(6)}
                DESCRIPTION	"The severity of DC Power failed alarm.
                me@zabbix:~$

If the query returns a value other than 1 (ok) it will fire the trigger

![alt text](https://github.com/hacktivism-github/zbx-templates-repository/blob/master/images/Screen%20Shot%202018-07-11%20at%2022.17.09.png "Logo Title Text 1")

![alt text](https://github.com/hacktivism-github/zbx-templates-repository/blob/master/images/Screen%20Shot%202018-07-11%20at%2022.14.02.png "Logo Title Text 1")

- Discovery: XTM Series::Equipment Status::Fan status

    - XTM Series | equipmentFanName $1
    - XTM Series | equipmentFanOperStatus $1
    - XTM Series | equipmentFanUnitFailed $1

        - Triggers:
            me@zabbix:~$ snmptranslate -m /usr/share/snmp/mibs/LUM-EQUIPMENT-MIB.txt -Td -Ib 'equipmentFanUnitFailed' | grep "TEX\|SYNT\|DESC"
            -- TEXTUAL CONVENTION FaultStatus
            SYNTAX	INTEGER {ok(1), alarm(2)}
            DESCRIPTION	"The fan module has failed or is absent.
            me@zabbix:~$
            
If the query returns a value other than 1 (ok) it will fire the trigger

![alt text](https://github.com/hacktivism-github/zbx-templates-repository/blob/master/images/Screen%20Shot%202018-07-11%20at%2022.38.20.png "Logo Title Text 1")

    
- Discovery: XTM Series::Equipment Status::Subrack Status

    - XTM Series | equipmentSubrackName $1
    - XTM Series | equipmentSubrackOperStatus $1
    - XTM Series | Equipment Subrack Temperature $1
    - XTM Series | Equipment Subrack Temperature Threshold $1
    - XTM Series | equipmentSubrackTempHighExceeded $1

- Discovery: XTM Series::Equipment Status::Board Configuration and Status

    - XTM Series | equipmentBoardName $1
    - XTM Series | equipmentBoardOperStatus $1
    - XTM Series | equipmentBoardUnderMaintenance $1

## Performance Measurements

- Discovery: XTM Series::PM EthTD::Current Meters and Configuration

    - XTM Series | pmEthTdName $1
    - XTM Series | Rx Ethernet Traffic Data on $1
    - XTM Series | Tx Ethernet Traffic Data on $1

## Optical Amplifiers
Note: Testing good with OA-RAED-21HG HYB and OA-20C-LG

- Discovery: XTM Series::Optical Amplifiers

    - XTM Series | OA interface $1
    - XTM Series | OA Operational State for the interface  $1
    - XTM Series | OA Adminintrative State for the interface  $1
    - XTM Series | OA Rx power level on $1
    - XTM Series | OA Tx power level on $1
    - XTM Series | OA Laser Bias High on $1
    - XTM Series | OA Loss Of Signal on $1
    - XTM Series | OA Output Power Fail on $1
    - XTM Series | OA Pump Laser Temp Low on $1
    - XTM Series | OA Received Power Low on $1
    - XTM Series | OA Rx Power Level Low Threshold on $1
    - XTM Series | OA Saturation Fault on $1
    - XTM Series | OA Tx Power Level Low Threshold on $1

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

![alt text](https://github.com/hacktivism-github/zbx-templates-repository/blob/master/images/Screen%20Shot%202018-07-10%20at%2021.49.42.png "Logo Title Text 1")

 

## License
This template is distributed under the terms of the GNU General Public License as published by the Free Software Foundation

## Copyright
Copyright (c) Bruno Filipe Teixeira
