# ZBX-CISCO-ASR9001-OPTICAL-MONITORING

The aim on to this "Template" its to simply monitor the Optical Levels on the transcievers being used on a Cisco ASR9000. It has been tested successfuly on the 9001 model but it is possible that it also works on the other models of the series.

[ASR9000](https://en.wikipedia.org/wiki/ASR9000)

All the items will reside on the so called Application by the name of "IOS-XR Optical Monitoring"

![alt text](https://github.com/hacktivism-github/zbx-templates-repository/blob/master/images/Screen%20Shot%202018-08-30%20at%2015.10.56.png "Logo Title Text 1")

- Discovery Rule:

discovery[{#SNMPVALUE},ENTITY-MIB::entPhysicalName]

Filters:
![alt text](https://github.com/hacktivism-github/zbx-templates-repository/blob/master/images/Screen%20Shot%202018-08-30%20at%2015.31.39.png "Logo Title Text 1")

Regular Expression:
![alt text](https://github.com/hacktivism-github/zbx-templates-repository/blob/master/images/Screen%20Shot%202018-08-30%20at%2015.32.18.png "Logo Title Text 1")

by: Vanilson Carvalho

- Triggers:

![alt text](https://github.com/hacktivism-github/zbx-templates-repository/blob/master/images/Screen%20Shot%202018-08-30%20at%2015.48.38.png "Logo Title Text 1")





## License
This template is distributed under the terms of the GNU General Public License as published by the Free Software Foundation

## Copyright
Copyright (c) Bruno Filipe Teixeira
