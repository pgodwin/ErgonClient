# ErgonClient
Ergon Energy API Client


# Swagger
https://www.homesmartsavvy.ergon.com.au/habi-ws-ergon/api/v1/swagger.json

# Base Url
https://www.homesmartsavvy.ergon.com.au/habi-ws-ergon/api/v1/

# EMS API

## Attributes

### Metering Attributes

The attributes recorded by the metering devices

<table border="1">

<tbody>

<tr>

<th>ID</th>

<th>Name</th>

<th>Units</th>

</tr>

<tr>

<td>201</td>

<td>Switch State</td>

<td>1=on, 0=off</td>

</tr>

<tr>

<td>202</td>

<td>Power</td>

<td>milli-watts</td>

</tr>

<tr>

<td>203</td>

<td>Voltage</td>

<td>milli-volts</td>

</tr>

<tr>

<td>205</td>

<td>Current</td>

<td>milli-amps</td>

</tr>

<tr>

<td>207</td>

<td>Power Factor</td>

<td>x1000</td>

</tr>

<tr>

<td>208</td>

<td>Frequency</td>

<td>milli-hertz</td>

</tr>

</tbody>

</table>

### Aggregation Attributes

The attributes computed for aggregations

<table border="1">

<tbody>

<tr>

<th>ID</th>

<th>Name</th>

<th>Units</th>

</tr>

<tr>

<td>202</td>

<td>Power</td>

<td>milli-watts</td>

</tr>

<tr>

<td>220</td>

<td>Dispatchable Power</td>

<td>milli-watts</td>

</tr>

<tr>

<td>221</td>

<td>Baseline Power</td>

<td>milli-watts</td>

</tr>

<tr>

<td>225</td>

<td>Apparent Power</td>

<td>milli-volt-amps</td>

</tr>

<tr>

<td>226</td>

<td>Dispatchable Apparent Power</td>

<td>milli-volt-amps</td>

</tr>

<tr>

<td>227</td>

<td>Baseline Apparent Power</td>

<td>milli-volt-amps</td>

</tr>

</tbody>

</table>

## Usage

The general usage of the API to obtain information relating to a user and their sites is:

1.  use the Token service to login and receive an authentication token.
2.  use the User service to retrieve information relating to the authenticated user.
3.  use the Site service to retrieve information relating to the authenticated user sites. This includes all the sites associated with the user (usually 1). The meters at the sites and energy attributes reported by the meters.

Examples:

1.  Authentication:

    <pre class="prettyprint">curl -i -H "Accept: application/json" -H "Content-Type: application/json" -X POST http://<host:port>/habi-ws-eddy/api/v1/token -d '{"userName":"<userName>", "password":"<password>"}'
               </pre>

    Response

    <pre class="prettyprint">HTTP/1.1 200 OK  

    Content-Type: application/json  

    Content-Length: 48  

    Date: Thu, 17 Mar 2016 03:35:01 GMT  

    {"token":"xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"}
               </pre>

2.  User:

    <pre class="prettyprint">curl -i -H "Accept: application/json" -H "Content-Type: application/json" -H "X-Auth-Token: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" -X GET http://<host:port>/habi-ws-eddy/api/v1/user
               </pre>

    Response

    <pre class="prettyprint">HTTP/1.1 200 OK  

    Content-Type: application/json  

    Content-Length: 109  

    Date: Thu, 17 Mar 2016 03:35:01 GMT  

    {"id":1,"userName":"<userName>","title":"<title>","firstName":"<firstName>","lastName":"<lastName>","mobileNo":"<mobileNo>","emailAddress":"<emailAddress>"}
               </pre>
