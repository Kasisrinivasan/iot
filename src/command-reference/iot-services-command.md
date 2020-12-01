### IoT Hub - Create/Delete & Properties display

##### IoT Hub - Create

```bash
az iot hub create --name <iothubName> -resource-group <resourceGroupName> \
     --sku <skuname>
```
For tier and pricing information refer to [documentation](https://azure.microsoft.com/en-us/pricing/details/iot-hub/).

##### IoT Hub - Delete

```bash
az iot hub delete --name <iothubName>  -resource-group <resourceGroupName>
```

##### IoT Hub - Properties Display 
```bash
az iot hub show --query properties.eventHubEndpoints.events.endpoint \
     --name <iothubName>

az iot hub show --query properties.eventHubEndpoints.events.path \
     --name <iothubName>

az iot hub policy show --name service --query primaryKey \
     --hub-name <iothubName>
```

##### IoT Hub - Retrieving Iot Hub Connection String 

```bash
az iot hub device-identity show-connection-string \
  --hub-name <iothubName> \
  --device-id <devicename> \
  --output table
```

##### IoT Hub - Retrieving Iot Hub Connection String (Backend Apps)

```bash
az iot hub show-connection-string --policy-name service \
     --name <iothubName> --output table
```

### IoT Hub - Device Registration

##### IoT Hub - Registering a Device

```bash
az iot hub device-identity create \
  --hub-name <iothubName> --device-id <devicename>
```

##### IoT Hub - Displaying a Connection String of the Device

```bash
az iot hub device-identity show-connection-string \
     --hub-name <iothubName> --device-id <devicename> --output table
```


### IoT Hub - Monitor

```bash
az iot hub monitor-events --output table --hub-name <iothubName>
```

### IoT Hub - IP Filter Rules

##### IoT Hub - Retrieve current IP filters 
```bash
az resource show -n <iothubName> -g <resourceGroupName> --resource-type Microsoft.Devices/IotHubs
```

##### IoT Hub - Add IP filters 
```bash
az resource update -n <iothubName> -g <resourceGroupName> \
     --resource-type Microsoft.Devices/IotHubs \
     --add properties.ipFilterRules "{\"action\":\"Reject\",\"filterName\":\"MaliciousIP\",\"ipMask\":\"6.6.6.6/6\"}"
```

##### IoT Hub - Delete IP filters 
```bash
az resource update -n <iothubName> -g <resourceGroupName> \
     --resource-type Microsoft.Devices/IotHubs \
      --add properties.ipFilterRules <ipFilterIndexToRemove>
```


### Routing

##### Create the route for the storage endpoint
```bash
az iot hub route create \
  --name $routeName \
  --hub-name $iotHubName \
  --source devicemessages \
  --resource-group $resourceGroup \
  --endpoint-name $endpointName \
  --enabled \
  --condition $condition
  ```
  
  ### Detailed Commands

* [az iot hub generate-sas-token](https://docs.microsoft.com/en-us/cli/azure/ext/azure-iot/iot/hub?view=azure-cli-latest#ext_azure_iot_az_iot_hub_generate_sas_token)

* [az iot hub monitor-events](https://docs.microsoft.com/en-us/cli/azure/ext/azure-iot/iot/hub?view=azure-cli-latest#ext_azure_iot_az_iot_hub_monitor_events)
