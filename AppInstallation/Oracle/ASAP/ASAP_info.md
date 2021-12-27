### stop and start
```
 stop_asap_sys -d && start_control_sys -d && start_asap_sys -d
 
 status
```
### Purge 
```
cleandata -d
```

### NE Config
```
installCartridge RIGHTEL_HSS.sar

```

### Others
```
172.20.32.13


OCA
1-OCA.cfg
config
	
SESSION
    HOST          172.20.32.13
    PORT          7001
    #SSL_PORT      7002
    ENV_ID        DEV
    SYSTEM_NAME   OCA_DEV
END_SESSION


asap_admin
Bonyan123

-----
cmws_studio
Bonyan123

http://172.20.32.13:7001/DEV/sadtConsole
-----

http://172.20.32.13:7001/DEV/OCA/
http://172.20.32.13:7001/DEV/Oracle/CGBU/Mslv/Asap/Ws
http://172.20.32.13:7001/DEV/Oracle/CGBU/Mslv/Asap/Ws?WSDL
http://172.20.32.13:7001/ws_utc/?wsdlUrl=http%3A%2F%2F172.20.32.13%3A7001%2FDEV%2FOracle%2FCGBU%2FMslv%2FAsap%2FWs%3FWSDL

```


#### Work Order Sample

http://172.20.32.13:7001/DEV/Oracle/CGBU/Mslv/Asap/Ws?WSDL

```
/app/asap/samples/jsrp/xml/

Username: asap_ws_user
Pass: Bonyan123
WSS-Password type: PasswordText
```

```
<?xml version="1.0" encoding="UTF-8"?>
<env:Envelope xmlns:env="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    
    <env:Body>
        <m:createOrderByValue
            xmlns:m="http://xmlns.oracle.com/communications/activation/asap/webservices">
<createOrderByValueRequest xmlns="http://java.sun.com/products/oss/xml/ServiceActivation" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:mslv-sa="http://www.metasolv.com/oss/ServiceActivation/2003" xmlns:co="http://java.sun.com/products/oss/xml/Common" xsi:schemaLocation="http://java.sun.com/products/oss/xml/ServiceActivation ../../xsd/XmlServiceActivationSchema.xsd http://www.metasolv.com/oss/ServiceActivation/2003 ../../xsd/ASAPServiceActivation.xsd">
        <orderValue xsi:type="mslv-sa:ASAPOrderValue">
                <apiClientId>Test</apiClientId>
                <orderKey>
                        <co:applicationContext>
                                <co:factoryClass/>
                                <co:url/>
                                <co:systemProperties/>
                        </co:applicationContext>
                        <co:type/>
                        <primaryKey/>
                </orderKey>
                <priority>3</priority>
                <requestedCompletionDate>2021-09-26T12:00:00</requestedCompletionDate>
                <services>
                        <item xsi:type="mslv-sa:ASAPService">
                                <serviceKey xsi:type="mslv-sa:ASAPServiceKey">
                                        <co:applicationContext>
                                                <co:factoryClass/>
                                                <co:url/>
                                                <co:systemProperties/>
                                        </co:applicationContext>
                                        <co:applicationDN>System/S225/ApplicationType/ServiceActivation/Application/1-0;7-3;ASAP/Comp/</co:applicationDN>
                                        <co:type/>
                                        <primaryKey>C_ZTE-HSS_1.2_ACT_DATA</primaryKey>
                                </serviceKey>
                                <mslv-sa:asdlRoute>TO_BE_DETERMINED</mslv-sa:asdlRoute>
                                <mslv-sa:serviceValues>
                                        <mslv-sa:serviceValue xsi:type="mslv-sa:ASAPServiceValue">
                                                <mslv-sa:name>MCLI</mslv-sa:name>
                                                <mslv-sa:value>N_ZTE-HSS_1.0_DEV</mslv-sa:value>
                                        </mslv-sa:serviceValue>
                                        <mslv-sa:serviceValue xsi:type="mslv-sa:ASAPServiceValue">
                                                <mslv-sa:name>MSISDN</mslv-sa:name>
                                                <mslv-sa:value>989203316531</mslv-sa:value>
                                        </mslv-sa:serviceValue>
                                </mslv-sa:serviceValues>
                        </item>
                </services>
                <mslv-sa:parentKey>
                        <co:applicationContext>
                                <co:factoryClass/>
                                <co:url/>
                                <co:systemProperties/>
                        </co:applicationContext>
                        <co:applicationDN/>
                        <co:type/>
                        <primaryKey/>
                </mslv-sa:parentKey>
                <mslv-sa:origin>ASC Test Orders</mslv-sa:origin>
                <mslv-sa:organizationUnit>POTS</mslv-sa:organizationUnit>
                <mslv-sa:timeout>0</mslv-sa:timeout><!-- Use Default -->
                <mslv-sa:secureData>true</mslv-sa:secureData>
                <mslv-sa:maximumDelayFail>0</mslv-sa:maximumDelayFail>
                <mslv-sa:rollbackIfFail>false</mslv-sa:rollbackIfFail>
                <mslv-sa:batchGroup/>
                <mslv-sa:asdlTimeout>0</mslv-sa:asdlTimeout> <!-- Use Default -->
                <mslv-sa:asdlRetry>5</mslv-sa:asdlRetry>
                <mslv-sa:asdlRetryInterval>120</mslv-sa:asdlRetryInterval>
                <mslv-sa:asdlDelayFail>false</mslv-sa:asdlDelayFail>
                <mslv-sa:externalSystemId/>
                <mslv-sa:srqAction>ADD</mslv-sa:srqAction>

                <mslv-sa:infoParms/>
                <mslv-sa:extendedWoProperties/>
        </orderValue>
</createOrderByValueRequest>
        </m:createOrderByValue>
    </env:Body>
</env:Envelope>

```
### build project 
add Build.xml under src
```
<?xml version="1.0"?>

<project default="package" basedir=".">
	<property name="basews" value="../../"/>
	<property name="jarTarget" value="${basews}/${project_name}/lib/${archive_name}.jar"/>
	<property name="outputDir" value="${basews}/${project_name}/out"/>
	
	<target name="package" depends="cleanPackage">
		<echo message="Project Name=${project_name}"/>
		<echo message="Destination Jar=${jarTarget}"/>
		<echo message="Output Dir=${outputDir}"/>
		<jar destfile="${jarTarget}" basedir="${outputDir}" filesonly="false"/>
	</target>
	
	<target name="cleanPackage">
		<echo message="Project Name=${project_name}"/>
		<delete file="${jarTarget}"/>
	</target>
</project>

```

Policy Override
```
x  ----  domain > configuration > web application > Allow all role

1- /app/mw/user_projects/domains/asap_domain/servers/AdminServer/upload/asapDEV/plan
2- ASAPPlan.xml
3- remove first variables
```
