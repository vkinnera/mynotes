# mynotes
 \vspace{-2pt} % Reduce space before the "Certifications" section

      \vspace{2pt} % Reduce space before the "Certifications" section

    \section{\textbf{Awards}}
    \vspace{1pt} 
     \begin{itemize}[left=0pt]
      \item Star performance - Capgemini \makebox[5.2in][r]{Feb 2024 - Feb 2024}
    \end{itemize}
    \vspace{-2pt} % Reduce space before the "Certifications" section
    
JSON PAYLOAD 
{
	"name": "kinnera",
	"age": 26
}

JSON PAYLOAD IN XML FORMAT

{
	"Details":
	{
  	"name": "kinnera",
	"age": 26
	}
}

XML PAYLOAD
<?xml version="1.0" encoding="UTF-8" ?>
 <root>
     <Details>
         <name>kinnera</name>
         <age>26</age>
     </Details>
 </root>
	
<?xml version="1.0" encoding="UTF-8" ?>
 <root>
     <name>kinnera</name>
     <age>26</age>
 </root>

%dw 2.0
output application/json
var life = "life is difficult"
fun CountryName(country_code) = if(country_code == "+91") ("India") 
    else  if(country_code == "+1")  ("USA")  else("other")
---
{
    "life": life,
    "countryName": CountryName("+1")
}

What is difference between function and variable in DW?
we cant pass input parameter  in variable but in function we can pass input parameter

%dw 2.0
output application/json
---
{
    "a": "dollor sign (\$)"
}
payload[0] first element in an array
payload[1] 2nd element in an array
payload[1 to -1] first to last element in an array
payload[-1] last element in an array

name space
%dw 2.0
output application/xml
ns h http://www.w3.org/TR/html4/
ns f https://www.w3schools.com/furniture
---
root:
{
    a: payload.root.h#table,
    b: payload.root.f#table
}
    

here .table gives first element in an xml payload, *table gives the entire payload in an 
input xml payload, h#table gives the particular namespace payload

what is traits and datatypes in mulesoft
resource is a collection of traits and data types
traits - headers, uriparams and queryParams are defined in traits
datatypes
 datatypes define structure of body it can define request or response like http status code
 200, 400 , 500 etc

what is difference between for each parallel for each and batch processing

for each process is single threaded and it process the records one by one and parallel for 
each is multi threaded and it process multiple records at the same time in parallel way

batch processing process the multiple records at the same time and it contains batch step - 
it contains processors and aggregators batch job and On complete stage

processors process the records based on accept policy and aggregrator combine the records.

in On Complete we do the meta data processing 

what is implementation URL
when we deploy mule application jar in cloud hub it generates one URL that is our implementation 
URL.
we use this URL with basepath to call an API.

to remove non funtional requirement 	(apply policy , SLA ) we can create proxy url on 
top of implementaion URL.

API auto discovery?
to connect the application deployed in mule runtime with API manager.
In cloud hub deployment we  have api manage where we apply policies and non functional requirements
In mule runtime where we deploy mule application code
if we want to connect application deployed in mule runtime we need auto discovery.
request - gateway - API Manager ( check and full fill policy and SLA )  if it is full fill it will go to
API Implementation in mule runtime.
API manager has this client Id enforcement.

difference  between v core and worker
v core is a unit of worker
worker is a smallest unit where we can deploy our mule application
0.1 vcore - 500 mb heap memory
0.2 vcore - 1gb heap memory
1 vcore - 2gb heap memory

MUNIT
Assert Operations
Assert: validate mule event content
equals
expression
that
mock when
mock event processor when it matches the defined name and attributes
spy
what happens when befor and after event process is called
verify
verify if the process is called
Fail
allow you to fail test case on purpose
behavior 
see all conditions before executing test logic.
mock and spy goes into this condition
execution 
meant for testing the logic which will wait for all the processess 	to get completed 
before executing the next scope
runs flow through this section	 
validation
assert and verify comes here to validate and verify the flow

allows you to set payload attributes and variables
normally defined at the beginning of the m unit test to define the first message to the 
set
 you can define many properties
 
 
 %dw 2.0
output application/json
---
{
    (
         ["1","2","3","4"] map ((item, index) -> 
(index): item
)
    )
} pluck ((value, key, index) -> (key+value):index)

%dw 2.0
output application/json
---
{
    "0": "1",

    "1": "2",

    "2": "3",

    "3": "4"
} pluck ((value, key, index) -> (key):value)
 what is pluck function and map function and mapObject?
 pluck function iterates over an object returns array of keys values and indices. - key value index
 map function iterates over an Array returns array - index, value
 mapObject iterates over an Object returns Object - key value index
 What is distinctBy?
 Iterates over an input and returns unique elements in it.
 
 What is joinBy function in Dataweave?
 merges an array into a single string value and uses the provided string as a separator between
 each item in the list.
 
 what is domain project?
 domain project is common mule project where we can keep all common mule resource 	which can be 
 used by multiple mule project which can be deployed in same runtime.
 
 we cant use domain project for cloud hub deployment model	since in cloud hub we deploy more than one
 project within same runtime that is worker.
 
 so it can be used only used in Onpremise deployment model.
 
 
why skipNullOn is used?
to skip all the null values from the respose


How to change date time in particular time Zone
now() >> "UTC"

how to format DateTime?
%dw 2.0
import * from dw::core::Strings
output json
---
(now() >> "IST") as String {format: "dd/mm/yyyy HH:mm:ss"}

How to reduce year by 1?
(now() >> 'UTC') - |P5Y|

(now() >> 'UTC') - |P5Y| - |P2M| - |P3D|

To reduce 2 hr 10 min 5sec
%dw 2.0
import * from dw::core::Strings
output json
---
(now() >> 'UTC') - |PT2H| - |PT10M| - |PT5S|


{
 "AU": ["PROD-202100BG12",
 "PROD-202100BG12",
 "PROD-202000BG12",
 "PROD-201900BG12"]
}

[
  {
    "Color": "Red",
    "Code": "#FF0000",
    "c":{
            "color": "darkRed"
    }
  },
  {
    "Color": "Green",
    "Code": "#00FF00"
  },
  {
    "Color": "Blue",
    "Color": "DarkBlue",
    "Code": "#0000FF"
  },
  {
    "Color": "Yellow",
    "Code": "#FFFF00"
  },
  {
    "Color": "Black",
    "Code": "#000000"
  },
  {
    "Color": "White",
    "Code": "#FFFFFF"
  }
]

dataweave selectors examples 
selecting color form 0 to 2 from the above payload  is payload[0 to 2].Color
selecting color from c  payload[0].c.color or selecting color from c in array payload..c.color
to select color payload payload.color and to print multiple key value pair in an object payload*.color
to select last element/object in an array payload[-1].color

Input
[
 {
 "name": "abc",
 "city" : "hyd"
 },
 {
 "name": "xyz",
 "city" : "delhi"
 },
 {
 "name": "abc1",
 "city" : "hyd"
 }
]
Output
"abc,abc1"

Dataweave code
%dw 2.0
import * from dw::core::Strings
output application/json
---
//payload[0].name ++ "," ++ payload[2].name

//((payload filter ((item, index) -> item.city == "hyd")).name)[0] ++ ',' ++ ((payload filter ((item, index) -> item.city == "hyd")).name)[1] 

((payload filter $.city == "hyd").name ) joinBy  (",")

how to call java code using dataweave?
create a package - org.mycompany.utils and create a class file in src/test/java folder
and create a class - with name Students
package org.mycompany.utils;

import java.util.Random;

public class Students {

    public static String appendRandom(String base) {
        return base + new Random().nextInt();
    }
}
to create access the class we use
%dw 2.0
import java!org::mycompany::utils::Students
output application/json
---
{
	a: Students::appendRandom("myString")	
}

floor function is used to rounds to nearest whole number
floor(14.99) is 14

how to get correlationId in mule
using the predefined variables 
%dw 2.0
output application/json
---
{
    flowname: flow.name,
    correlation: correlationId,
    appName: app.name
}
we can use those predefined variables for logging purpose only 


charCode
Returns an UNI code for the first character in the input String
CharCodeAt 	- returns unicode for a character at a specified Index
charCodeFrom - returns the character that matches the specified Unicode.
Input:
{
 "ASCII Value": 65,
 "Char at ASCII": "A"
}
Output:
{
  "ASCII Value": 65,
  "Char at ASCII": 65,
  "Char at ASCII": "A"
}
Dataweave:
%dw 2.0
import * from dw::core::Strings
output application/json
---
{
    "ASCII Value": charCode(payload."Char at ASCII"),
    "Char at ASCII": charCodeAt(payload."Char at ASCII",0),
    "Char at ASCII": fromCharCode(payload."ASCII Value" as Number)
}

create a variable in DW
%dw 2.0
output application/json
var myVar = "Dataweave"
---
myVar
 
 create a function in dw and example
 creating a function uses fun key word and input arguments and logic
 	%dw 2.0
output application/json
fun test(p: String) = 
 "foo" ++ p 
---
test(" bar")
output: "foo bar"

writing a else if in Dataweave
%dw 2.0
output application/json
var currency = "USD"
---
country: if(currency == "USD") "USA" else if(currency == "EURO") "france" else ""

output: USA

to not print empty we use default keyword
%dw 2.0
output application/json
---
payload[0].Color  default "white"

endsWith function in dataweave?

returns true if a string ends with a provided substring, false if not.
input
["a.csv","b.csv","c.xlsx","d.docx","e.docx"]
output
[
  "a.csv",
  "b.csv",
  "c.xlsx"
]
Dataweave code
%dw 2.0
output application/json
---
//payload filter ((item, index) -> item != "d.docx" and item != "e.docx")
payload filter(($ endsWith("csv") )or ($ endsWith("xlsx") ))

how to encrpt string value in dataweave using md5 algorithm?
%dw 2.0
import dw::Crypto
output application/json
---
{"md5": Crypto::MD5("asd" as Binary)}
output:{
  "md5": "7815696ecbf1c96e6894b779456d330e"
}

what is multi part in dataweave
%dw 2.0
import dw::module::Multipart
output multipart/form-data
var myOrder = [
  {
    order: 1,
    amount: 2
  },
  {
    order: 32,
    amount: 1
  }
]
var myClients = {
  clients: {
    client: {
      id: 1,
      name: "Mariano"
    },
    client: {
      id: 2,
      name: "Shoki"
    }
  }
}
---
{
  parts: {
    order: Multipart::field({name:"order",value: myOrder, mime: "application/json", fileName: "order.json"}),
    clients: Multipart::field({name:"clients", value: myClients, mime: "application/xml"})
  }
}
output:
------=_Part_3955_1942853238.1722103735207
Content-Type: application/json
Content-Disposition: form-data; name="order"; filename="order.json"

[
  {
    "order": 1,
    "amount": 2
  },
  {
    "order": 32,
    "amount": 1
  }
]
------=_Part_3955_1942853238.1722103735207
Content-Type: application/xml
Content-Disposition: form-data; name="clients"

<clients>
  <client>
    <id>1</id>
    <name>Mariano</name>
  </client>
  <client>
    <id>2</id>
    <name>Shoki</name>
  </client>
</clients>
------=_Part_3955_1942853238.1722103735207--


what is contains?
Returns true if an input contains a given value, false if not.
input:
{
 "a" : ["12", "15", "17"] ,
 "b":["15", "18", "20", "12" , "89"]
}
dataweave
%dw 2.0
import * from dw::core::Strings
output application/json
---
//payload.a filter ((item, index) -> item !="17")
payload.a filter(payload.b contains $)
output
[
  "12",
  "15"
]
remove a key value pair in an Object?
{
 "fname":"a",
 "lname":"b",
 "age":"23"
}
DW code: payload - "fname" - "lname"
output: {
  "age": "23"
}

adding a increment value to key ?
input:
[{
 "name": "a"
 },
 {
 "name": "b"
 }
]
output:[
  {
    "user0": "a"
  },
  {
    "user1": "b"
  }
]
DW: %dw 2.0
output application/json
---
payload map ((item, index) -> 
  ('user' ++ index): item.name
)


what is filterObject in Mule?
Iterates a list of key-value pairs in an object and applies an expression 
that returns only matching objects, filtering out the rest from the output.
example:
input:
{
"arrivalDateTime": "",
"cabin": {},
"fareComponent": [],
"flightNumber": "3234",
}
output:
{
  "flightNumber": "3234"
}
Dataweave:
%dw 2.0
output application/json
---
payload filterObject ((value, key, index) -> 
sizeOf(value) !=0
)

how to read content in a file?
%dw 2.0
var myJsonSnippet = readUrl("classpath://json_file/test.json", "application/json")
output application/json
---
myJsonSnippet


Convert Current Data & Time to a Specific Time Zone
now() >> "IST"


what is read in dw?
Reads a string or binary and returns parsed content.
how to parse a String into a particular format?
dw:%dw 2.0
output application/xml
---
read('{ "hello" : "world" }','application/json')
output:
<?xml version='1.0' encoding='UTF-8'?>
<hello>world</hello>

Checks if the text contains only Unicode digits.
DW:%dw 2.0
import * from dw::core::Strings
output application/json
---
payload.number splitBy("") filter(isNumeric($))

find the available TZ's for data time conversion?


what is reduce function in dw?
Applies a reduction expression to the elements in an array.



API LIFE CYCLE?
--> create RAML - RESTFUL API MODELLING LANGUAGE  - we provide resource, input, output, datatype
-> 	Publish RAML to exchange
-> Review RAML and getting the feedback
-> if positive - build stage else go to design stage ie., RAML 
-> In build stage we do the API development.
-> After development of API we do the testing stage - MUNIT testing
->  we will secure API's applying policy like client id enforcement, ratelimiting etc
-> After deploying in cloudHub -> 	we should moniter application in cloudHub 
--> troubleshooting - bugs and then managing the API's

Available timezones for datatime converstion?
java!java::util::TimeZone::getAvailableIDs()

CICD or how do deploy
code - write scripts regarding  the jenkins file - it will take that code from the repo
build the code - after build it deploy on server.

once code is checkin it will deployed on server or if we need to deploy in UAT OR QA after code checkin 
we need approval and after approval we will deploy into the server.

devops teams writes pipeline scripts and we will deploy the code in jenkins by using the jenkins file.

what are the policies that you ave worked on?

Ratelimiting(throttling) - rate limiting is used to control the number of api call 
we can call the external system and the external system has some limit if the more than 
limited req will come then we will get out of memory as error message.

Spike control (throttling)- It is similar to rate limiting but we define the size of queue what ever the size
of queue if the size of queue is completed we will take another queue.

basic auth - 
client Id enforcement - 
JWT token - 
Oauth - 
HTTP Caching - 


how to call subflow file using dataweave
file - readURL
flow - lookUp


how to call configure properties in dw
p('propertyname')

when we use VM connector flow, where do we use
to use VM queue provided from the mulesoft.

Rate limiting is the way where we limit the number of request from the user side 
429 limit exceeded.

throtlling
maximum number of reqests that can be processed with in a given time frame the excess request can be 	
can be managed, cancelled or processed in some other way
we use mule cache component first time we call from the external system then we will get the
response from cache.

Mulesoft API end to end process. 

traits vs fragments. 

how do we do validation in raml. 

how do we hand over raml to client after designing. 

post vs put vs  patch. 

need of put & post. 

foreach vs parallel foreach   

scatter-gather. 

spike control vs rate limiting policy. 

Munits. 

  deployment model (through jenkinspipeline).   

vcore vs worker. 

error handling. 

VM vs flow refference. 

Active MQ. 

issues faced in production,deployment. 

object store,cache. 

load balancer. 

data weave (string to array, reverse, multivalue selector). 

scenario based questions on try scope,scatter-gather, re-connection stratgy. 


self Intro 

roles and responsibilites in project 


message structure in IBM mq? 

default port no for IBM mq? 

what are the basic steps to develop an API? 

how can you secure your password? 

what is the pooling mechanism? it is like how can you secure a password 

what are the 5 ways of security authentications 

what is TLS and MTLS? 

what is the keyStore and trustStore? 

error handlings in mule?  

have you heard about API Groups? 

  

have you develop any custom connector? 

  

dataweave streaming in mule? 

  

xplain Oauth2.0 provider in mule? why we are using? 

  

what are grant Types in Oauth2.0? 

  

rate limiting policy? 

  

what is horizontal and vertical scaling? 

  

xplain batch processing? 

  

what happens if a batch is having 200 records if one got failed? 

  

how many records can we process in a batch? 

  

can we call batch fom trigger? 

  

map vs mapObject? 

  

what is Idempotency?what is this use 

  

what is scheduler? 

  

which flow can we call from lookup function? 

  

how to handel error in process layer? 

  

what is the output for for each? 

  

what is the file we used to secure password? 

  

what is CI/Cd pipeline?have you used in your project? 

  

how to improve the performance of an application? 

  

how do you setup the dependencies in your project? 

  

if you need to save the state of the transaction and then resume it if it fails? 

what is synchronous and asynchronous?  

what is diff b/w api kit router and api ki console? 
  
can we validate the incoming payload from RAML? 

what dataweave inbuild functions you used? 

how can we call flows from dataweave? 

have you involved in documentation side or deployment side? 

have you created any proxys in api manager? 

 mulesoft interview 

mulesoft interview 

total feilds  

self Intro 
Components in raml? 
api life cycle 
whats are the ways to import raml to studio and explain them 
apikit console --scenario based 
api exchange, cloudhub --scenario based 
how scaling can be done 
about logs --scenario based 
dataweave -- on map, odd even, pluck in playground 
diff between rest and soap 
parallel for each --scenario based 
database connector --scenario based 
batch processing --scenario based 
http listner configurations 
policies used in project 
how do you protect your code in project 
how do you get api instance id 
how do you connect your runtime api to configure policies 
how do you generate flows in studio if they are not generated automatically 
error handling --scenario based 
Type of error handling used in your project 
api led connectivity --scenario based 
salesforce connector 
cache and object store 
munits in project 
flows in project 
ssl and tls 
keystore and Truststore and how do you get keys 
how to configure ssl and tls in listner 
how do you update raml and impor 

  

  



---------------------RAML------------------------------- 
title 
baseUri 
/resource: 
  method  
 
 
Data Type can be referred using "!include" keyword  from fragments 
Library is a collection of dataTypes -- library should be imported using "usage" keyword(by creating an object in it) and it is referred 
Example can be referred using "!include" keyword  from fragments 
Traits is used for headers and queryParameters -- Traits should be imported using "Traits" keyword(by creating key: !include filePath) and it is referred using "is" keyword with these[]( is:[headersname,.....,...] 

  

------------------------------------------------------------------------- 
For properties files 
Syntax- 
http.port=8081 

  

To read from properties file - ${http.port} 
when we clicked on fx(dataweave) - Mule::P('http.port') 

  

  

For Yaml files 
Syntax- 
http: 
   port: "8081" 
 
To read from properties file - ${http.port} 
when we clicked on fx(dataweave) - Mule::P('http.port') 

  

  

Secure properties generator for encrypting secure password 
In global elements create new Secure properties configuration for decrypting the key 
when using Secure properties configuration 
To read from properties file - ${secure::http.port} 
when we clicked on fx(dataweave) - Mule::P('secure::http.port') 

  

  

parallel ForEach - o/p- the output of this scope is the collection of the results of each route and the aggregated results will be in the same order they were, prior to the split. 
for each - o/p same orginal payload it doesnt modify the payload 
batch processing- Summary report 
scatter gather- an aggregated response of the routes 

  

  

watermarking-- to avoid duplicate data processing   

  

i have worked on a api called Post refund in which we have used api led connectivity structure 
in these we have three layers 
redmound ux as experience layers 
payment management biz as process layer 
aria management sys as a system layer 
in this we get inputs from frontend called fastgo payments 

  

From the frontend we get required inputs like business id, payment id, targetSystem which are passed into the ux, 
In ux we do the validations for inputs and later it is routed to the biz layer using request connector. 

  

In payement management biz depending upon the business id and target system we will route it to the sys layer 

  

aria management system is connected to the backend and retrive the data, 
in this we mapped using transform message and created a request to the backend to get the account no and details which is required for refund 
after getting the acc details we have done the validations for date. 
after the validations are done and again we mapped with the account details and payement id using transform message and created request to the backend 
now the refund is done from the backend and we get response like "refund is Intiated". 

  

 

transform message takes the request message and transformed into required mule format. 

SOAP - simple object access protocol 

REST - Representational state transfer 

It is a XML based protocol for accessing web services and it is platform independent and language independent. 

SOAP uses WSDL file and Rest uses RAML OR SWAGGER FILE. 

MAP and MAP object 

map fun is used to go through the element in array - to process multiple record in JSON array 

mapObject is to go through keys and values in each of the objects of the array - to process multiple object in record(array) 

mulesoft interview
 
total feilds 

transform message takes the request message and transformed into required mule format.
SOAP - simple object access protocol
REST - Representational state transfer
It is a XML based protocol for accessing web services and it is platform independent and language independent.
SOAP uses WSDL file and Rest uses RAML OR SWAGGER FILE.
MAP and MAP object
map fun is used to go through the element in array - to process multiple record in JSON array
mapObject is to go through keys and values in each of the objects of the array - to process multiple object in record(array)

connector in MULE?
connector is used to connect with the external system. it can be file, FTP, SFTP, DB connector.

what is transform message?
transform mule component transform message coverts from one format to another format with the help of mule expression.

What is SOAP?
SOAP is a Simple Object Access protocal - it is as XML based protocol for accessing the web services. SOAP is W3C 
recommandations for communication between applications. it is a platform independent and language independent.

SOAP is protocol and Rest is a architecture
Soap contains WSDL file and rest contains RAML.

Difference between map and mapObject?
map is used to go through multiple objects in an array and mapObject goes through multiple objects.
MAP function takes the input as an array and in mapObject takes input as an object

%dw 2.0
output json
---
[{"a":"b","c":"d"} mapObject () -> { ($$$) : { ($$):$} }]
//$$ - key, $ - value, $$$ - index
++
["a", "b", "c"] map () -> {($$):($)}
//$$ - key, $ - value

parallel for we manage the threads
batchprocessing process based on vcore

if there is any failure in particular system in scatter gather component then we use try block and on error continue
the retrive the value 
payload.0.payload
payload.1.payload	

XA transsaction participate in (JMS DB)
NON XA transaction(file, FTP, SFTP, HTTP)

senario:I have a input payload before for each 1,2,3. I have done addition like payload + 10. what is payload of for each
ANS: 
foreach
payload after and before for each - same
Variable after and before for each - changes(what ever we will configure in last loop )
parallel for each
payload after and before parallel for each - changes(collection of all payload in parallel for each)
variable after and before for each - same

the variable created inside the parallel for each will not exists after parallel for each

if I had two tables where i wanted to retrive data 	which are not dependent on each other. Then how  to handle it.
use scatter gather  and create two branch to call DB table.
POST:/accounts/{accountNo}/rollbackBasicPlan

capgemini:

basic Auth:
we provide the user id and password to the client to access an API.

client Id enforcement
It is generally used for ux api's to secure our API's from different vendors.

each vendor has their own set of client Id and client secret.
 
 what is JWT token/Oath in mulesoft?
 
 generally we use these token in ux api's. they provide robust security.
 We need third party like Oath , it is like handshaking process. we will call the third party and they will provide the JWT token 
 and we will use thay third party to use our API.
 
 when ever we will configure out JWT token they will use their private key and we will use their public key to encrpt that
 particular token and we will see that paricular token is valid or not. if the token is not valid we will throw error message
 if it valid token allow them to call our API.

 it used to securly trasmit information between the parties as a JSON object. 
 This information can be verified and trusted because it is digitally signed. 
 JWTs are commonly used for authentication and authorization purposes.
 
 
HTTP CACHING
http caching is checked in the gate way level only. it checks the whether the api contains caching or not if it presents 
it will continue the flow.

difference b/w ratelimiting and throtelling?
ratelimiting limits the number of req's and trotking caches the req's. it handles the overwehming req's adjust the load based on input requests.


what are error handling components?
on error continue:
it ill handle error and throw 200 as response and continue to next flow
on error propagate
it ill handle error and throw 500 error
raise error
raise error is used to handle custom errors or to create manual error or business error

what is vertical scaling vs horizantal scaling?
vertical scaling - increasing number of v cores
it ill handle more number of requests and bigger size payload
horizantal scaling - increasing number of workers


what is thread pool and auto tuning?
It is a collection of threads and that will created based on number of v core and size of memory
Auto tuning increases the number of v core based on input requests.


what is munit?
Using munit we can automate our testing process in mulesoft similar to junit in java.
Using munit we check our code coverage and we can handle error in munit.

what is parallel for each?
variable before parallel foreach and after parallel for each is same and payload before and after changes.

what is async scope?
when ever we want handle a component in a separate thread we will use the ASYNC scope.


traits:
for calling the external traits we will use is: [] keyword.A trait can have all kinds of attributes.
examples:
examples contain sample input request and sample output response.

how many types of deployment available in mule application?
cloudhub - runtime plane and management plane 
onpremise - runtime plane and management plane both will be managed by customer itself.
hybrid - it runtime is customer hosted and management plane will be mulesoft hosted.
RTF - docker and kubernates are inbuilt in RTF.

how many ways to deploy mule application?
we have multiple way
way1:
we will deploy mule applcation as a jar then go to the runtime plane and uplaod the jar.
way2:
through anypoint studio.
way3:
we deploy api using CICD pipeline.

where do we deploy 
we deploy our code through mule runtime in cloudHub.

what is choice router?
we can create multiple branch will based condition only one branch will be executed.

What is scatter gather?
scatter 

Munit testing?
code coverage and automating our testing process similar to JUNIT.

domain project?
it can be used in customer hosted domain project. we can use this domain. 
in domain project we can configure like common resources like common error handlers and global error handlers, property file
domain project is only used in on premise deployment model.

why we connot deploy our domain project mule application in cloud hub?
because if we create domain project in one worker another worker cannot use domain project.


security policy?
client ID enforcement
JWT token
Oath

dataweave to remove empty values in an Object.
input:
{
"arrivalDateTime": "",
"cabin": {},
"fareComponent": [],
"flightNumber": "3234",
}
Script:
%dw 2.0
output application/json
---
//payload filterObject ((value, key, index) -> !isEmpty(value))
payload filterObject ((value, key, index) -> sizeOf(value)!=0 )
output:
{
  "flightNumber": "3234"
}

API monitering?
how many request are coming and how many threads are consuming and how many memory usage are there which external system taking how much time.


project exaplanation?
this question is combination of API LED Architecture and API development lifecycle.


Oath ?
check internet
we get the Oath token from the customer by creating the Oath API where we configuring the input request payload with client id secret audience, grantType
  then we will get the access token and then we will give that access token to key Authorization, value - bearer to call our API.
  
  
what is reduce function?
Applies a reduction expression to the elements in an array.
input:
[
 {
 "id1":"101",
 "name1":"shubham"
 },
 {
 "id2":"102",
 "name2":"mule"
 }
]
Script:
%dw 2.0
import * from dw::core::Strings
output application/json 
---
payload reduce($ ++ $$)
output:
{
  "id2": "102",
  "name2": "mule",
  "id1": "101",
  "name1": "shubham"
}


What is maxBy?
Iterates over an array and returns the highest value of Comparable elements from it.
Input:[{
 "Name": "Shubham",
 "Marks":"95"
}, {
 "Name": "Shubh",
 "Marks":"65"
}, {
 "Name": "SC",
 "Marks":"70"
}]
script:%dw 2.0
//import * from dw::core::Strings
output application/json 
---
payload maxBy ((item) -> item.Marks)
output:
{
  "Name": "Shubham",
  "Marks": "95"
}

Difference between “not” & “!” operator?

not operator works on the result of overall logical operation but ! works on the first result of logical operation
example:
Input{
 "x":true,
 "y":false
}
Script:
%dw 2.0
import * from dw::core::Strings
output application/json 
---
{
    "r1": not payload.x and payload.y == true,
    "r2": !payload.x and payload.y == true
    
}
output:
{
  "r1": true,
  "r2": false
}

format data
input: <placedDate>2022-05-25 00:00:00.0</placedDate>
%dw 2.0
var x = (payload.placedDate splitBy  ' ')[0]
output application/json
---
x as Date {format : "yyyy-MM-dd"} as String {format: "dd/MM/yyyy"}
output:"25/05/2022"

Oath policy we will use for security purpose 
when request will come then it call Oath service provider their we will get the token then we will call API  then API will call Oath server 
to validate that token.

we will make three call to send request to mule API.

how do we call API form differnt layers.?
generally we will call an API using HTTP requestor connector
form process to system and from experience to process layer 
generally we will call using HTTP requestor.
some time we develop connector like we create create for system layer and publish to exchange.
use that connector in process layer.

Object store ?
performance increases in Object strore.
In object store we value in the form of key value pair.

handle errors in batch processing?
In batch processing we store error message in batch step component.


distinctBy is used to remove all the duplicate values.


if there is three branch in scatter gather and one of the branch is throwing error we use try block to catch the error.
all the mule component placed in block.

payload.0.payload gives the first branch payload. in scatter gather.


Iam getting multiple similar requests from end users I have rate limiting policy as 100 requests per minute 
Idont want to keep waiting 	users I dont want to send request errors to users how to handle.
ans: cache scope

In batch processing we have 100 records and 10 records failed. I want to send failed records status to end user.
In batch processing error based records in one batch step and failed records in another batch step

what is RAML?
RAML - restful API modelling language. we create RAML for documentation work of our API
it has 
baseUri
Resource - in resouce we have resourcename, method used 
Request - in request we have Headers, Queryparams, body, URI PARAMS
Response - response payload
Underlying dataType - datatype for request and response like TEXT, JSON, XML and SO On


what is trait?
traits is reusable component where we can define headers, queryParams, URI params inside traits.

what is dataType?
It is a structuere / schema of request and response datatype
datType consists of schema of request and response payload.

what is resourceType?
resource is collection of traits and datTypes.

what is fragment?
fragment is a shared repo which can be used by multiple RAML's. like if we define traits inside RAML it ill used only on that
RAML and if we define in fragment we use that in multiple RAML's.


what is flatten and reduce funtion in dataweave?
for reduce function input is array and output is an Object.
it contains item - $ - value of each iteration. 
and acummulator - $$ - is the initial value/ combined value/ result of each iteration
Example:
%dw 2.0
output application/json
---
"a": [1, 2, 3, 4] reduce ($+$$)
Output:  "a": 10
%dw 2.0 
output application/json
---
"a": [1, 2, 3, 4] reduce ($++$$)
Output: "a": 1234

flatten:
Input of an flatten function is an array and output is array.
It combines two or more array of objects into single array of objects
or particular element inside of array of object into a single array
%dw 2.0
output application/json
var array1 = [1,2,3]
var array2 = [4,5,6]
var array3 = [7,8,9]
var arrayOfArrays = [array1, array2, array3]
---
flatten(arrayOfArrays)
Output
[ 1,2,3,4,5,6,7,8,9 ]

how can we call a file, flow ?
for file we can use the readUrl
for flow we can use the lookup function

worker?
worker is the smallest unit of mule runtime where wew deploy our mule application.
we need atleast one worker to deploy mule application.

vcore is the capacity of worker.

v core(veritical scaling) or worker(horizantal scaling) is the way to increase the capacity of application

deployment strategy
repository which repo we  are using
continuous integration and continous deployment
when ever we commit our code then CICD will take our code build that code and deploy that code on mule runtime server.

once we done in local testing then we move into dev env by using the CICD script and move into dev to SIT.

TLS vs SSL
HTTP connector https protocal then we can secure our REST API using our ssl protocol
it can be two way SSL or one way
in one way who will API they need call your API key 
and our side we configure the public key.

In two way SSL, we will share the public key to calling system and calling will send their public their pubic key to
configure your http listener.


authentication and authorization?
Authentication user Id and password 
authorization 
you have permission to use those userId and password or not.


what is API manager and auto discovery?
when ever we want connect with mule runtime with API manager in cloud hub we use API auto discovery and the can configured in mule application.
once it configure API manager there we can configure policies.

where you will configure mule properties?

key value pairs

secure property
we can encrpt that particular property and then we place our value inside our property file.


mask function?
This mask function replaces all simple elements that match the specified criteria.
%dw 2.0
import * from dw::util::Values
output application/json
---
payload mask field("CreditCard") with  "****_****_****"
input:{
 "CreditCard":"4567–1234–9087"
}
output:{
  "CreditCard": "****_****_****"
}


extract URI parameters or value form the URL.
Input:{ 
 "url":"https://xyz.com/api/Emp/999"
}
Output:"999"
DW:%dw 2.0
import * from dw::core::Arrays
output application/json
---
//((payload.url splitBy  "/" ) filter ((item, index) -> item == "999"))[0]
//slice(payload.url splitBy  (/[\/]/), 5,6)[0]

what is target variable?
 if we keep target variable as payload in database connector then outcome of database is payload.
 if we set the target variable name then the payload value is assigned to target variable.
 it will reduce the space complexity of the xml if the set the payload in the target variable.	
 variable and payload is not safe
 
 
Assign Array Key to Each Array Value?
Input:-
{
"Date" : [
"01/05/1991",
"31/01/1995"
]
}
Output:-
{
 "Date": "31/01/1995",
 "Date": "01/05/1991"
}
dw:
%dw 2.0
var Ip = (payload.Date map ((item, index) -> {
    "Date": item
})) 
output application/json
---
Ip reduce ((item, accumulator) -> item ++ accumulator)

Async Scope:
we use the Async to call the subflow asychronously.
go for sysnc scope if and only if we want execute some logic that is independent form other flow.
the scope of async scope is stateless. Async scope never changes our payload and never initialize set variable in ASYNC Scope.
variable and payload is not safe

try:
try with the On error continue wont give the error, variable and payload.
but try with the On error propagate give the error, variable and payload.

until SuccessFul?
if a connector is failing then until successFul is used to retry until the connector executes successfully without any error.

it is good to keep until successful component in asynchronous flows	
it is not recommended to keep the until successful in synchronous flows like restAPI's.



divideBy:
(dw::core::Arrays)Breaks up an array into sub-arrays that contain the specified number of elements.
(dw::core::Objects)Breaks up an object into sub-objects that contain the specified number of key-value pairs.
input:{
 "Name": "Shubham",
 "Marks": 90,
 "Name": "AShish",
 "Marks": 50,
 "Name": "Divya",
 "Marks": 80
}
output:
[
  {
    "Name": "Shubham",
    "Marks": 90
  },
  {
    "Name": "AShish",
    "Marks": 50
  },
  {
    "Name": "Divya",
    "Marks": 80
  }
]
dw:
%dw 2.0
import * from dw::core::Objects
output application/json
---
payload divideBy 2

underscore:
Replaces hyphens, spaces, and camel-casing in a string with underscores.
Input:-
"casualPlaces-required Yes"
Output:-
"casual_places_required_yes"
Dataweave Code:-
%dw 2.0
import * from dw::core::Strings
---
underscore(payload)

Dynamic Value of Key in Key-Value Pair:
Input:[
{
"Source": " customerName",
"destination": " customer "
},
{
"Source": " customerAddress",
"destination": " address"
}
]
Output:{
  "a": {
    " customer ": " address"
  },
  "b": {
    " customerAddress": " address",
    " customerName": " customer "
  }
}
DW:%dw 2.0
output application/json
---
{
    a:(payload[0].destination): payload[1].destination,
b:payload map ((item, index) -> {
    (item.Source):item.destination
})reduce ((item, accumulator) -> item ++ accumulator)
}

SOAP SERVICE?
WSDL - web service description language that defines the soap service



hi everyone 
I am vamsi
Iam from nellore 
i studies tech ece from svce in tirupathi 
I have 3 + years I have 2\+ years relevent experience in mulesoft 
of experience in capgemini
Currently i was serving as mulesoft developer in capgemini and serviing client called CWC - cable and wireless
for that particular client I am working in project called cco digital
and my resposibity in capegemini is to develop design and testing API's 
my project follows API life cycle to develop API's














 






	










 
