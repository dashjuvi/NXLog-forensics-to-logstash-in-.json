# NXLog
NXLog configuration to send the logs to our server outside the VM
* [NXLog](https://nxlog.co/documentation/nxlog-user-guide) - Tool used

# Getting Started

First, download NXLog or copy this repository to get everything you need to get started,
no need for further dependencies

# Conf

List of changes made to NXLog config to set up everything

## We gonna use the .json format to parse into elasticsearch bd
```
<Extension json>
    Module  xm_json
</Extension>
```

## Also getting the Operational, System, Security and Application logs to compare with ours.
```
<Select Path="Microsoft-Windows-Sysmon/Operational">*</Select> \
			<Select Path="System">*</Select> \
			<Select Path="Security">*</Select> \
			<Select Path="Application">*</Select> \
```

## List of the top relevant IDs events, we can found more info in the microsoft page of each of them.
```
or $EventID == 100 \
	or $EventID == 101 \
	or $EventID == 104 \
	or $EventID == 104 \
	or $EventID == 105 \
	or $EventID == 106 \
	or $EventID == 305 \
	or $EventID == 1000 \
	or $EventID == 1102 \
	or $EventID == 3065 \
	or $EventID == 3066 \
	or $EventID == 4070 \
	or $EventID == 4075 \
	or $EventID == 4624 \
	or $EventID == 4625 \
	or $EventID == 4634 \
	or $EventID == 4648 \
	or $EventID == 4688 \
	or $EventID == 4728 \
	or $EventID == 4732 \
	or $EventID == 4735 \
	or $EventID == 4740 \
	or $EventID == 4756 \
	or $EventID == 4768 \
	or $EventID == 4769 \
	or $EventID == 4776 \
	or $EventID == 5140 \
	or $EventID == 7022 \
	or $EventID == 7023 \
	or $EventID == 7024 \
	or $EventID == 7026 \
	or $EventID == 7031 \
	or $EventID == 7032 \
	or $EventID == 7034 \
	or $EventID == 7040 \
	or $EventID == 7045 
  ```
  
  ## Output
  Using ssl, could use the om_tmp too. Port to feed logstash 5140 default!
  Host ip from outside. (The server one)
   ```
  Module om_ssl
	Port 5140
	Host 10.3.150.38
	CAFile C:\Program Files\nxlog\cert\logstash_CA.pem
   ```
