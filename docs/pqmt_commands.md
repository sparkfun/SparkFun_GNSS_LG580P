Below, are excerpts for a few of the PQTM messages from the [GNSS Protocol Specification](./assets/component_documentation/quectel_lg290p03lgx80p03_gnss_protocol_specification_v1-1.pdf) manual. Users will find these useful for configuring their LG580P GNSS module as an RTK base station or rover.

???+ info "Documentation"
	A full list of PQTM messages (proprietary NMEA messages defined by Quectel) supported by LG580P, is provided in section **2.3. PQTM Messages** of the [GNSS Protocol Specification](./assets/component_documentation/quectel_lg290p03lgx80p03_gnss_protocol_specification_v1-1.pdf) manual. This protocol is used to configure or read the settings for the LG580P GNSS module.

	??? abstract "List of Proprietary Quectel Messages"
		<article style="text-align: center;" markdown>

		| Message                             | Type Mode    | Message Description                              |
		| :---------------------------------- | :----------: | :----------------------------------------------- |
		| PQTMVER                             | Output       | Outputs the firmware version                     |
		| PQTMCOLD                            | Command      | Performs a cold start                            |
		| PQTMWARM                            | Command      | Performs a warm start                            |
		| PQTMHOT                             | Command      | Performs a hot start                             |
		| PQTMSRR                             | Command      | Performs a system reset and reboots the receiver |
		| PQTMUNIQID                          | Command      | Queries the module unique ID                     |
		| [PQTMSAVEPAR](#pqtmsavepar)         | Command      | Saves the configurations into NVM                |
		| [PQTMRESTOREPAR](#pqtmrestorepar)   | Command      | Restores the parameters configured by all commands to their default values |
		| PQTMVERNO                           | Command      | Queries the firmware version                     |
		| [PQTMCFGUART](#pqtmcfguart)         | Set/Get      | Sets/gets the UART interface                     |
		| PQTMCFGPPS                          | Set/Get      | Sets/gets the PPS feature                        |
		| [PQTMCFGPROT](#pqtmcfgprot)         | Set/Get      | Sets/gets the input and output protocol for a specified port |
		| PQTMCFGNMEADP                       | Set/Get      | Sets/gets the decimal places of standard NMEA messages |
		| PQTMEPE                             | Output       | Outputs the estimated position error             |
		| PQTMCFGMSGRATE                      | Set/Get      | Sets/gets the message output rate on the current interface |
		| PQTMVEL                             | Output       | Outputs the velocity information                 |
		| PQTMCFGGEOFENCE                     | Set/Get      | Sets/gets geofence feature                       |
		| PQTMGEOFENCESTATUS                  | Output       | Outputs the geofence status                      |
		| PQTMGNSSSTART                       | Command      | Starts GNSS engine                               |
		| PQTMGNSSSTOP                        | Command      | Stops GNSS engine                                |
		| PQTMTXT                             | Output       | Outputs short text messages                      |
		| [PQTMCFGSVIN](#pqtmcfgsvin)         | Set/Get      | Sets/gets the Survey-in feature                  |
		| PQTMSVINSTATUS                      | Output       | Outputs the Survey-in status                     |
		| PQTMPVT                             | Output       | Outputs the PVT (GNSS only) result               |
		| [PQTMCFGRCVRMODE](#pqtmcfgrcvrmode) | Set/Get      | Sets/gets the receiver working mode              |
		| PQTMDEBUGON                         | Command      | Enables debug log output                         |
		| PQTMDEBUGOFF                        | Command      | Disables debug log output                        |
		| PQTMCFGFIXRATE                      | Set/Get      | Sets/gets the fix interval                       |
		| [PQTMCFGRTK](#pqtmcfgrtk)           | Set/Get      | Sets/gets the RTK mode                           |
		| PQTMCFGCNST                         | Set/Get      | Sets/gets the constellation configuration        |
		| PQTMDOP                             | Output       | Outputs dilution of precision                    |
		| PQTMPL                              | Output       | Outputs protection level information             |
		| PQTMCFGODO                          | Set/Get      | Sets/gets the odometer feature                   |
		| PQTMRESETODO                        | Command      | Resets the accumulated distance recorded by the odometer |
		| PQTMODO                             | Output       | Outputs the odometer information                 |
		| PQTMCFGSIGNAL                       | Set/Get      | Sets/gets GNSS signal mask                       |
		| PQTMCFGSAT                          | Set/Get      | Sets/gets GNSS satellite mask                    |
		| PQTMCFGRSID                         | Set/Get      | Sets/gets the reference station ID               |
		| PQTMCFGRTCM                         | Set/Get      | Sets/gets RTCM                                   |
		| PQTMCFGSBAS                         | Set/Get      | Configures SBAS                                  |
		| PQTMCFGNMEATID                      | Set/Get      | Configures the NMEA Talker ID                    |
		| PQTMTAR                             | Output       | Outputs the time and attitude                    |
		| PQTMCFGBLD                          | Set/Get      | Configures the baseline distance                 |
		| PQTMCFGRTKSRCTYPE                   | Set/Get      | Configures RTK differential source type          |
		| PQTMSN                              | Command      | Reads the SN of module                           |
		| PQTMCFGANTINF                       | Set/Get      | Configures the antenna information               |
		| PQTMCFGANTDELTA                     | Set/Get      | Configures the delta between antennas            |
		| PQTMCFGSIGGRP                       | Set/Get      | Configures the GNSS signal group                 |
		| PQTMCFGSIGNAL2                      | Set/Get      | Configures GNSS signal mask for second antenna   |
		| PQTMCFGGEOSEP                       | Set/Get      | Configures geoidal separation                    |
		| PQTMCFGCNRTHD                       | Set/Get      | Configures the CNR threshold for position engine |
		| PQTMCFGELETHD                       | Set/Get      | Configures the elevation threshold for position engine |
		| PQTMNAV                             | Output       | Outputs the navigation information               |
		| PQTMEOE                             | Output       | Outputs the end of epoch information             |
		| PQTMCFGWN                           | Set/Get      | Configures the reference start week number       |
		| PQTMANTENNASTATUS                   | Output       | Reports the antenna status                       |


		</article>


## Save Parameters/Restore to Default Settings


#### `PQTMSAVEPAR`
:   Saves the current configurations into NVM of the LG580P

	```
	$PQTMSAVEPAR*<Checksum><CR><LF>
	```


	??? example
		Save the current settings to non-volatile memory of the LG580P.
		```
		$PQTMSAVEPAR*5A
		```

		If there are no errors, users will receive the following response:
		```
		$PQTMSAVEPAR,OK*72
		```


#### `PQTMRESTOREPAR`
:   Restores the parameters configured by all commands to their default values; this command takes effect after restarting the LG580P

	```
	$PQTMRESTOREPAR*<Checksum><CR><LF>	
	```


	??? example
		Restore all the settings of the LG580P to their factory defaults
		```
		$PQTMRESTOREPAR*13
		```

		If there are no errors, users will receive the following response:
		```
		$PQTMRESTOREPAR,OK*3B
		```


## UART Settings


#### `PQTMCFGUART`
:   Configures the serial protocol setting for the UART interfaces

	- Current UART interface:

		```
		$PQTMCFGUART,W,<BaudRate>[,<DataBit>,<Parity>,<StopBit>,<FlowCtrl>]*<Checksum><CR><LF>
		```

	- A specific UART interface:

		```
		$PQTMCFGUART,W,<Index>,<BaudRate>[,<DataBit>,<Parity>,<StopBit>,<FlowCtrl>]*<Checksum><CR><LF>
		```


	**Parameters:**

	<table markdown>
	<tr markdown>
	<th>Field</th>
	<td markdown>`<Index>`</td>
	<td markdown>`<BaudRate>`</td>
	<td markdown>`<DataBit>`</td>
	<td markdown>`<Parity>`</td>
	<td markdown>`<StopBit>`</td>
	<td markdown>`<FlowCtrl>`</td>
	</tr>
	<tr markdown>
	<th>Description</th>
	<td markdown>
	**UART Interface**
	<ul markdown>
	<li markdown>`1` = UART1</li>
	<li markdown>`2` = UART2</li>
	<li markdown>`3` = UART3</li>
	</ul>
	</td>
	<td markdown>
	**Baud Rate** (bps)
	<ul markdown>
	<li markdown>`9600`</li>
	<li markdown>`115200`</li>
	<li markdown>`230400`</li>
	<li markdown>==`460800`==</li>
	<li markdown>`921600`</li>
	</ul>
	</td>
	<td markdown>
	**Number of Data Bits**
	<ul markdown>
	<li markdown>==`8` = 8 bits==</li>
	</ul>
	</td>
	<td markdown>
	**Parity**
	<ul markdown>
	<li markdown>==`0` = No parity==</li>
	<li markdown>`1` = Odd parity</li>
	<li markdown>`2` = Even parity</li>
	<li markdown>`3` = Mark</li>
	<li markdown>`4` = Space</li>
	</ul>
	</td>
	<td markdown>
	**Number of Stop Bit**(s)
	<ul markdown>
	<li markdown>==`1` = 1 stop bit==</li>
	<li markdown>`2` = 2 stop bits</li>
	</ul>
	</td>
	<td markdown>
	**Flow Control**
	<ul markdown>
	<li markdown>==`0` = None==</li>
	</ul>
	</td>
	</tr>
	</table>


	???+ tip "Baud Rate"
		For ports utilized in conjunction with either the BlueSMiRF or radio transceivers, we recommend reducing the baud rate to 115200bps or lower to avoid overflowing the buffers of the transceiver's serial port.


	??? example "Configure the Settings"
		!!! abstract inline end "Example Settings"

			- Port: `UART1`
			- Baud Rate: 115200bps
			- Data Bits: 8
			- Parity: No
			- Stop Bits: 1
			- Flow Control: None

		Configure the baud rate of the current UART interface to 115200bps:
		```
		$PQTMCFGUART,W,115200*18
		```

		Configure the baud rate of `UART1` to 115200bps:
		```
		$PQTMCFGUART,W,1,115200*05
		```

		Configure all parameters of the current UART interface:
		```
		$PQTMCFGUART,W,115200,8,0,1,0*11
		```

		Configure all parameters of `UART1`:
		```
		$PQTMCFGUART,W,1,115200,8,0,1,0*0C
		```

		If there are no errors, users will receive the following response:
		```
		$PQTMCFGUART,OK*60
		```


	??? example "Retrieve the Settings"
		!!! abstract inline end "Example Settings"

			- Port: `UART1`
			- Baud Rate: 115200bps
			- Data Bits: 8
			- Parity: No
			- Stop Bits: 1
			- Flow Control: None

		Get the configuration on the current UART interface:
		```
		$PQTMCFGUART,R*36
		```

		Get the configuration on UART1:
		```
		$PQTMCFGUART,R,1*2B
		```

		If there are no errors, users will receive the following response:
		```
		$PQTMCFGUART,OK,1,115200,8,0,1,0*5F
		```


#### `PQTMCFGPROT`
:   Configures the input/output protocol on a specified port

	```
	$PQTMCFGPROT,W,<PortType>,<PortID>,<InputProt>,<OutputProt>*<Checksum><CR><LF>
	```


	**Parameters:**

	<table markdown>
	<tr markdown>
	<th>Field</th>
	<td markdown>`<PortType>`</td>
	<td markdown>`<PortID>`</td>
	<td markdown>`<InputProt>`</td>
	<td markdown>`<OutputProt>`</td>
	</tr>
	<tr markdown>
	<th>Description</th>
	<td markdown>
	**Port Type**
	<ul markdown>
	<li markdown>==`1` = UART==</li>
	</ul>
	</td>
	<td markdown>
	**Port ID**
	<ul markdown>
	<li markdown>`1` = UART1</li>
	<li markdown>`2` = UART2</li>
	<li markdown>`3` = UART3</li>
	</ul>
	</td>
	<td colspan="2" markdown>
	**Input/Output Protocols** (`HEX`: 32-bit)
	<ul markdown>
	<li markdown>==Bit `0` = NMEA==</li>
	<li markdown>==Bit `2` = RTCM3==</li>
	</ul>
	The **default** protocols are NMEA and RTCM3:<br>
	==**HEX:** `00000005`==<br>
	**BIN:** `0000 0000 0000 0000 0000 0000 0000 0101`
	</td>
	</tr>
	</table>


	??? example "Configure the Settings"
		!!! abstract inline end "Example Settings"

			- Port: `UART1`
			- Input Protocol: NMEA & RTCM3
			- Input Protocol: NMEA & RTCM3

		Configure the configuration on UART1:
		```
		$PQTMCFGPROT,W,1,1,00000005,00000005*38
		```

		If there are no errors, users will receive the following response:
		```
		$PQTMCFGPROT,OK*6B
		```


	??? example "Retrieve the Settings"
		!!! abstract inline end "Example Settings"

			- Port: `UART1`
			- Input Protocol: NMEA & RTCM3
			- Input Protocol: NMEA & RTCM3

		Get the configuration on UART1:
		```
		$PQTMCFGPROT,R,1,1*3D
		```

		If there are no errors, users will receive the following response:
		```
		$PQTMCFGPROT,OK,1,1,00000005,00000005*6B
		```


## RTK Settings


#### `PQTMCFGSVIN`
:   Configures a base station's position either by **survey-in** mode or **fixed** mode

	```
	$PQTMCFGSVIN,W,<Mode>,<CFG_CNT>,<3D_AccLimit>,<ECEF_X>,<ECEF_Y>,<ECEF_Z>*<Checksum><CR><LF>
	```


	**Parameters:**

	<table markdown>
	<tr markdown>
	<th>Field</th>
	<td markdown>`<Mode>`</td>
	<td markdown>`<CFG_CNT>`</td>
	<td markdown>`<3D_AccLimit>`</td>
	<td markdown>`<ECEF_X>` `<ECEF_Y>` `<ECEF_Z>`</td>
	</tr>
	<tr markdown>
	<th>Description</th>
	<td markdown>
	**Receiver Mode**
	<ul markdown>
	<li markdown>==`0` = Disable==</li>
	<li markdown>`1` = Survey-in mode</li>
	<li markdown>`2` = Fixed mode<br>*(Position is configured in ECEF coordinates)*</li>
	</ul>
	</td>
	<td markdown>
	**Survey-in Mode**<br>
	Minimum positioning time *(seconds)*
	<ul markdown>
	<li markdown>Range: `0`-`86400`</li>
	<li markdown>==**Default:** `0`==</li>
	</ul>
	</td>
	<td markdown>
	**Survey-in Mode**<br>
	3D positioning accuracy *(meters)*
	<ul markdown>
	<li markdown>`0` = No limit</li>
	<li markdown>==**Default:** `0.0`==</li>
	</ul>
	</td>
	<td markdown>
	**Fixed Mode**<br>
	WGS84 ECEF X,Y,Z coordinates *(meters)*
	<ul markdown>
	<li markdown>==**Default:** `0.0000`==</li>
	</ul>
	</td>
	</tr>
	</table>


	???+ info "RTK Base Station Modes"
		In order to operate as a base station, the LG580P GNSS module requires an accurate position of its antenna. This can be either defined in [ECEF coordinates](https://en.wikipedia.org/wiki/Earth-centered%2C_Earth-fixed_coordinate_system) or acquired through a self-survey process.

		1. ==Survey-In Mode:== The base station's location is established based on a weighted mean of recent solutions of its position. The `<CFG_CNT>` and `<3D_AccLimit>` parameters define the shortest amount of time that the position gets surveyed and the maximum standard deviation of the estimated position.
		1. ==Fixed Mode:== The base station's position is provided in [ECEF coordinates](https://en.wikipedia.org/wiki/Earth-centered%2C_Earth-fixed_coordinate_system).
	
		!!! note
			Any error in the base station's location will translate directly into an error in the rover's position.


	??? example "Configure the Settings"
		!!! abstract inline end "Example Settings"

			- Mode: Survey-in mode
			- Survey Time: 3600 seconds
			- 3D Accuracy: 1.2m
			- ECEF Coordinates:
				- X: -2519265.0514m
				- Y: 4849534.9045m
				- Z: 3277834.6432m

		Configure the configuration on UART1:
		```
		$PQTMCFGSVIN,W,1,3600,1.2,-2519265.0514,4849534.9045,3277834.6432*01
		```

		If there are no errors, users will receive the following response:
		```
		$PQTMCFGSVIN,OK*70
		```


	??? example "Retrieve the Settings"
		!!! abstract inline end "Example Settings"

			- Mode: Survey-in mode
			- Survey Time: 3600 seconds
			- 3D Accuracy: 1.2m
			- ECEF Coordinates:
				- X: -2519265.0514m
				- Y: 4849534.9045m
				- Z: 3277834.6432m

		Get the configuration on UART1:
		```
		$PQTMCFGSVIN,R*26
		```

		If there are no errors, users will receive the following response:
		```
		$PQTMCFGSVIN,OK,1,3600,1.2,-2519265.0514,4849534.9045,3277834.6432*52
		```


#### `PQTMCFGRCVRMODE`
:   Configures the mode that the receiver is operating in

	```
	$PQTMCFGRCVRMODE,W,<Mode>*<Checksum><CR><LF>
	```


	**Parameters:**

	<table markdown>
	<tr markdown>
	<th>Field</th>
	<td markdown>`<Mode>`</td>
	</tr>
	<tr markdown>
	<th>Description</th>
	<td markdown>
	**Operation mode**
	<ul markdown>
	<li markdown>`0` = Unknown</li>
	<li markdown>
	**`1` = Rover**<br>
	When set to this mode, the receiver will restore to default NMEA message output state.
	</li>
	<li markdown>`2` = Base Station<br>
	When set to this mode, the receiver will automatically disable NMEA message output and enable RTCM `MSM4` and RTCMv3 `1005` message output.
	</li>
	</ul>
	</td>
	</tr>
	</table>


	!!! note
		After switching the module‘s working mode, save the configuration and then reset the module. Otherwise, it will continue to operate in the original mode.


	??? example "Configure the Settings"
		!!! abstract inline end "Example Settings"

			- Port ID: `UART1`
			- Input Protocol: NMEA & RTCM3
			- Input Protocol: NMEA & RTCM3

		Configure the configuration on UART1:
		```
		$PQTMCFGRCVRMODE,W,2*29
		```

		If there are no errors, users will receive the following response:
		```
		$PQTMCFGRCVRMODE,OK*64
		```


	??? example "Retrieve the Settings"
		!!! abstract inline end "Example Settings"

			- Port ID: `UART1`
			- Input Protocol: NMEA & RTCM3
			- Input Protocol: NMEA & RTCM3

		Get the configuration on UART1:
		```
		$PQTMCFGRCVRMODE,R*32
		```

		If there are no errors, users will receive the following response:
		```
		$PQTMCFGRCVRMODE,OK,2*7A
		```


#### `PQTMCFGRTK`
:   Configures the operation settings of the RTK mode

	```
	$PQTMCFGRTK,W,<DiffMode>,<RelMode>*<Checksum><CR><LF>
	```


	**Parameters:**

	<table markdown>
	<tr markdown>
	<th>Field</th>
	<td markdown>`<DiffMode>`</td>
	<td markdown>`<RelMode>`</td>
	</tr>
	<tr markdown>
	<th>Description</th>
	<td markdown>
	**Differential Mode**
	<ul markdown>
	<li markdown>`0` = Disable RTK/RTD feature *(Differential data is not used)*</li>
	<li markdown>**`1` = Auto mode**</li>
	<li markdown>`2` = RTD only mode *(Only pseudoranges is used)*</li>
	</ul>
	</td>
	<td markdown>
	**Absolute/Relative Mode**
	<ul markdown>
	<li markdown>**`1` = Absolute mode, ensure absolute position accuracy**</li>
	<li markdown>`2` = Relative mode, ensure relative position accuracy</li>
	</ul>
	This field only takes effect when `<DiffMode>` = `1` and the module enters the RTK only mode.
	</td>
	</tr>
	</table>


	??? example "Configure the Settings"
		!!! abstract inline end "Example Settings"

			- Port ID: `UART1`
			- Input Protocol: NMEA & RTCM3
			- Input Protocol: NMEA & RTCM3

		Configure the configuration on UART1:
		```
		$PQTMCFGRTK,W,1,1*6C
		```

		If there are no errors, users will receive the following response:
		```
		$PQTMCFGRTK,OK*3F
		```


	??? example "Retrieve the Settings"
		!!! abstract inline end "Example Settings"

			- Port ID: `UART1`
			- Input Protocol: NMEA & RTCM3
			- Input Protocol: NMEA & RTCM3

		Get the configuration on UART1:
		```
		$PQTMCFGRTK,R*69
		```

		If there are no errors, users will receive the following response:
		```
		$PQTMCFGRTK,OK,1,1*3F
		```



## Heading Settings


### `PQTMTAR`
:   Outputs the time and attitude. The attitude computation in this message is computed from the two-antenna system.

	```
	$PQTMTAR,<MsgVer>,<Time>,<Quality>,<Res>,<Length>,<Pitch>,<Roll>,<Heading>,<Acc_Pitch>,<Acc_Roll>,<Acc_Heading>,<UsedSV>*<Checksum><CR><LF>
	```


	**Parameters:**

	<table markdown>
	<tr markdown>
	<th>Field</th>
	<th>Description</th>
	</tr>
	<tr markdown>
	<td markdown>`<MsgVer>`</td>
	<td markdown>
	**Message version.**
	<ul markdown>
	<li markdown>`1` = Version 1 (Always `1` for this message version)</li>
	</ul>
	</td>
	</tr>
	<tr markdown>
	<td markdown>`<Time>`</td>
	<td markdown>
	**UTC Time** *(`hhmmss.ddd`)*
	<ul markdown>
	<li markdown>`hh` = Hours (24hr)</li>
	<li markdown>`mm` = Minutes</li>
	<li markdown>`ss` = Seconds</li>
	<li markdown>`ddd` = Milliseconds</li>
	</ul>
	</td>
	</tr>
	<tr markdown>
	<td markdown>`<Quality>`</td>
	<td markdown>
	**GPS Heading Quality**
	<ul markdown>
	<li markdown>`0` = Fix not available or invalid</li>
	<li markdown>`1` = GPS SPS Mode, fix valid</li>
	<li markdown>`2` = Differential GPS, SPS Mode, or Satellite Based Augmentation System (SBAS), fix valid</li>
	<li markdown>`3` = GPS PPS Mode, fix valid</li>
	<li markdown>`4` = Fix Heading. System used in RTK mode with fixed integers</li>
	<li markdown>`5` = Float Heading. Satellite system used in RTK mode, floating integers</li>
	</ul>
	</td>
	</tr>
	<tr markdown>
	<td markdown>`<Res>`</td>
	<td markdown>
	**Reserved**
	</td>
	</tr>
	<tr markdown>
	<td markdown>`<Length>`</td>
	<td markdown>
	**Baseline Length** *(meters)*
	</td>
	</tr>
	<tr markdown>
	<td markdown>`<Pitch>`</td>
	<td markdown>
	**Pitch Angle** *(degrees)*
	<ul markdown>
	<li markdown>Range: `-90.000000`-`90.000000`</li>
	</ul>
	</td>
	</tr>
	<tr markdown>
	<td markdown>`<Roll>`</td>
	<td markdown>
	**Roll Angle** *(degrees)*
	<ul markdown>
	<li markdown>Range: `-180.000000`-`180.000000`</li>
	</ul>
	</td>
	</tr>
	<tr markdown>
	<td markdown>`<Heading>`</td>
	<td markdown>
	**Heading** *(degrees)*
	<ul markdown>
	<li markdown>Range: `0.000000`-`360.000000`</li>
	</ul>
	</td>
	</tr>
	<tr markdown>
	<td markdown>`<Acc_Pitch>`</td>
	<td markdown>
	**Pitch Accuracy** *(degrees)*
	</td>
	</tr>
	<tr markdown>
	<td markdown>`<Acc_Roll>`</td>
	<td markdown>
	**Roll Accuracy** *(degrees)*
	</td>
	</tr>
	<tr markdown>
	<td markdown>`<Acc_Heading>`</td>
	<td markdown>
	**Heading Accuracy** *(degrees)*
	</td>
	</tr>
	<tr markdown>
	<td markdown>`<UsedSV>`</td>
	<td markdown>
	**Satellites**<br>
	Number used for heading solution
	</td>
	</tr>
	</table>


	!!! info
		- Only the LG580P supports this message
		- More information for the direction of `<Heading>` in the `$PQTMTAR` message, please refer to the [dual-antenna heading application note](./assets/component_documentation/quectel_lg580p_series_dual-antenna_heading_application_note_v1-0.pdf)



	??? example "Parsed Message"
		```
		$PQTMTAR,1,165034.000,4,,0.860,1.124780,1.254125,50.968541,0.254125,0.125485,0.012547,21*52

		```

		- Message Version: `1`
		- UTC Time: 16:50 34.000s
		- GPS Heading Quality: `4` - Fix Heading. System used in RTK mode with fixed integers
		- Baseline Length: 0.860m
		- Pitch Angle: 1.124780&deg;
		- Roll Angle: 1.254125&deg;
		- Heading: 50.968541&deg;
		- Pitch Accuracy: 0.254125&deg;
		- Roll Accuracy: 0.125485&deg;
		- Heading Accuracy: 0.012547&deg;
		- Satellites: `21`



### `PQTMCFGBLD`
:   Configures the baseline distance between the two antennas.

	```
	$PQTMCFGBLD,W,<Distance>*<Checksum><CR><LF>
	```


	**Parameters:**

	<table markdown>
	<tr markdown>
	<th>Field</th>
	<td markdown>`<Distance>`</td>
	</tr>
	<tr markdown>
	<th>Description</th>
	<td markdown>
	**Baseline Distance** *(meters)*
	<ul markdown>
	<li markdown>Range: `0.000`-`5.000`</li>
	<li markdown>==**Default:** `0.000`==</li>
	</ul>
	When the baseline distance is `0`, the baseline distance will calculate by software
	</td>
	</tr>
	</table>


	!!! info
		- Only the LG580P supports this message


	??? example "Configure the Settings"
		!!! abstract inline end "Example Settings"

			- Port ID: `UART1`
			- Input Protocol: NMEA & RTCM3
			- Input Protocol: NMEA & RTCM3

		Configure the configuration on UART1:
		```
		$PQTMCFGBLD,W,1.000*68
		```

		If there are no errors, users will receive the following response:
		```
		$PQTMCFGBLD,OK*38
		```


	??? example "Retrieve the Settings"
		!!! abstract inline end "Example Settings"

			- Port ID: `UART1`
			- Input Protocol: NMEA & RTCM3
			- Input Protocol: NMEA & RTCM3

		Get the configuration on UART1:
		```
		$PQTMCFGBLD,R*6E
		```

		If there are no errors, users will receive the following response:
		```
		$PQTMCFGBLD,OK,1.000*3B
		```
