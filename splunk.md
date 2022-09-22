## Some queries to try out with Splunk  
#### Query for HTTP Status codes  
index=cba_stargate URI=*myurl/resource/endpoint1* OR URI=*myurl/resource/endpoint2* | chart count by HTTPStatus  

#### Query to check for 9 second timeouts  
Getting a 504? Might be related to a backend service in the gateway timing out  
index=cba_stargate URI=*myurl/resource/endpoint1* OR URI=*myurl/resource/endpoint2* AND HTTPStatus=504   

#### Query between endpoints  
index=cba_stargate URI=*myurl/resource/endpoint1* OR URI=*myurl/resource/endpoint2* AND HTTPStatus=504 | chart count by host  

#### Query upstream service issue  
index=cba_stargate URI=*myurl/resource/endpoint1* OR URI=*myurl/resource/endpoint2* AND HTTPStatus=504| chart count by ServiceName  

#### Splunk Query for Backend Latency  
index=cba_stargate URI=*myurl/resource/endpoint1* OR URI=*myurl/resource/endpoint2* | timechart p50(BackendLatency) p95(BackendLatency) p99(BackendLatency)  

