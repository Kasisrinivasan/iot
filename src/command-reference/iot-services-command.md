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

##### IoT Hub - Retrieve current IP filters 
```bash
az resource show -n <iothubName> -g <resourceGroupName> --resource-type Microsoft.Devices/IotHubs
```

##### IoT Hub - Add IP filters 
```bash
az resource update -n <iothubName> -g <resourceGroupName> --resource-type Microsoft.Devices/IotHubs \
     --add properties.ipFilterRules "{\"action\":\"Reject\",\"filterName\":\"MaliciousIP\",\"ipMask\":\"6.6.6.6/6\"}"
```

##### IoT Hub - Delete IP filters 
```bash
az resource update -n <iothubName> -g <resourceGroupName> --resource-type Microsoft.Devices/IotHubs \
      --add properties.ipFilterRules <ipFilterIndexToRemove>
```
