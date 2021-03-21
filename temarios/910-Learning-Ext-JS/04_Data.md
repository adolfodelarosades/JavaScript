# 4. Acerca de los Datos
* Ajax
   * Pasar parámetros a Ajax request
   * Configuración del timeout para las llamadas a Ajax request
* Modelos
    * Mapeos
    * Validadores
    * Tipos de campos personalizados
    * Relaciones
       * Asociaciones One-to-many
       * Asociaciones One-to-one
* Trabajando con store
    * Añadiendo nuevos elementos
    * Recorrer los records/models en el store.
    * Recuperar los records en el store
       * Por posición de índice
       * Primer y último registro
       * Por rango
       * Por ID
    * Eliminación de registros
* Recuperando datos remotos
   * Ajax proxy
   * Readers
      * XML reader(Lector XML)
* Enviando datos
* Resumen

En este capítulo, aprenderemos sobre el uso del data package en Ext JS. Además, hablaremos sobre Ajax, Data Models, Data Stores y los lreaders y writers disponibles que podemos usar para almacenar nuestros datos localmente.

El data package es lo que nos permitirá cargar y guardar datos en nuestro código o aplicaciones. Es importante tener una comprensión sólida del data package para que podamos vincular o vincular datos en componentes Ext JS. El data package contiene varias clases para manejar datos, pero hay algunas clases principales que se utilizarán casi siempre. Eche un vistazo a la siguiente figura:

![04-01](images/04-01.png)

Ext JS crea una capa abstracta con muchas clases y configuraciones; la idea es utilizar estas clases cuando se trata de información. Todos los widgets y componentes que muestran información utilizan el data package para manipular y presentar los datos fácilmente.

> **NOTA**
> 

## Ajax

```js
Ext.Ajax.request({
   url:"serverside/myfirstdata.json"
});
console.log("Next lines of code...");
```

> **NOTA**
> 

```js
Ext.Ajax.request({
   url:"serverside/myfirstdata.json",
   success: function(response,options){
      console.log('success function executed, here we can do some stuff !');
   },
   failure: function(response,options){
      Ext.Msg.alert("Message", 'server-side failure with status code ' + response.status);
   },
   callback: function( options, success, response ){
      console.log('Callback executed, we can do some stuff !');
   }
});
```

```js
{
   "success": true,
   "msg": "This is a success message..!"
}
```

> **TIP**
> 

```js
success: function(response,options){
   var data = Ext.decode(response.responseText);
   Ext.Msg.alert("Message", data.msg);
},
```

```js
Ext.Ajax.request({
  url: "serverside/myfirstdata.json ",
  success: function(response,options){
    console.log('success function executed, here we can do some stuff !');
  },
  failure: function(response,options){
    console.log('server-side failure with status code ' + response.status);
  },
  callback: function( options, success, response ){
    if(success){
      var data= Ext.decode(response.responseText);
      Ext.Msg.alert("Message", data.msg);
    }
  }
});
```

> **TIP**
> 

![04-02](images/04-02.png)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<response success="true">
<msg>This is a success message in XML format</msg>
</response>
```

```js
Ext.Ajax.request({
  url: "serverside/myfirstdata.xml",
  success: function(response,options){
    var data = response.responseXML;
    var node = xml.getElementsByTagName('msg')[0];
    Ext.Msg.alert("Message", node.firstChild.data );
  },
  failure: function(response,options){
    Ext.Msg.alert("Message", 'server-side failure with status code ' + response.status);
  }
});
```

### Pasar parámetros a Ajax request

```js
Ext.Ajax.request({
  url: "serverside/myfirstparams.php",
  method: 'POST',
  params: {
    x:200,
    y:300
  },
  success: function(response,options){
    var data = Ext.decode(response.responseText);
    Ext.Msg.alert("Message", data.msg);
  },
  failure: function(response,options){
    Ext.Msg.alert("Message", 'server-side failure with status code' + response.status);
    Ext.Msg.alert("Message", 'server-side failure:' + response.status);
  }
});
```

![04-03](images/04-03.png)

> **TIP**
> 

### Configuración de timeout para las llamadas a Ajax request

```js
Ext.Ajax.request({
  url: "serverside/myfirstparams.php",
  method: 'POST',
  params: {x:200, y:300},
  timeout: 50000,
  success: function(response,options){
    var data = Ext.decode(response.responseText);
    Ext.Msg.alert("Message", data.msg);
  },
  failure: function(response,options){
    Ext.Msg.alert("Message", 'server-side failure with status code ' + response.status);
    Ext.Msg.alert("Message", 'server-side failure:' + response.status);
  }
});
```

> **TIP**
> 

## Modelos

> **NOTA:**
> 

```js
Ext.define('Myapp.model.Client',{
extend:'Ext.data.Model',  // step 1
idProperty:'clientId ', // step 2
fields:[// step 3
  {name: 'clientId', type: 'int'},
  {name: 'name'    , type: 'string'},
  {name: 'phone'   , type: 'string'},
  {name: 'website' , type: 'string'},
  {name: 'status'  , type: 'string'},
  {name: 'clientSince', type: 'date', dateFormat:'Y-m-d H:i'}
]
});
```

> **NOTA:**
> 

```js
var myclient = Ext.create('Myapp.model.Client',{
  clientId:10001,
  name:'Acme corp',
  phone:'+52-01-55-4444-3210',
  website:'www.acmecorp.com',
  status:'Active',
  clientSince:'2010-01-01 14:35'
});
console.log(myclient);
console.log("My client's name is = " + myclient.data.name);
console.log("My client's website is = " + myclient.data.name);
```

```js
// GET METHODS
var nameClient = myclient.get('name');
var websiteClient = myclient.get('website');
console.log("My client's info= " + nameClient + " - " + websiteClient);

// SET Methods
myclient.set('phone','+52-01-55-0001-8888'); // single value
console.log("My client's new phone is = " + myclient.get('phone'));
myclient.set({ //Multiple values
  name: 'Acme Corp of AMERICA LTD.',
  website:'www.acmecorp.net'
});
console.log("My client's name changed to = " + myclient.get("name"));
console.log("My client's website changed to = " + myclient.get("website") );
```

```js
//READ
console.log("My client's name:" + myclient.data.name);
console.log("My client's website:" + myclient.data.website);
// Write
myclient.data.name = "Acme Corp ASIA LTD.";
myclient.data.website = "www.acmecorp.biz";
```

```js
//READ
console.log("My client's name:" + myclient.get("name"));
console.log("My client's website:" + myclient.get("website"));
// Write
myclient.set("name", "Acme Corp ASIA LTD. ");
myclient.set("website", "www.acmecorp.biz");
```

### Mapeos

```js
{
  "success" :"true",
  "id":"id",
  "records":[
    {
      "id": 10001,
      "name": "Acme corp2",
      "phone": "+52-01-55-4444-3210",
      "x0001":"acme_file.pdf"
    }

  ]
}
```

```js
Ext.define('Myapp.model.Client',{
extend: 'Ext.data.Model',
idProperty: 'clientId ',
fields:[
  {name: 'clientId', type: 'int'  },
  {name: 'name'    , type: 'string'},
  {name: 'phone'   , type: 'string'},
  {name: 'contractFileName', type: 'string', mapping:'x0001'}
]
});
```

![04-04](images/04-04.png)

### Validadores

```js
Ext.define('Myapp.model.Client',{
extend:'Ext.data.Model',
idProperty:'clientId ',
fields:[
  {name: 'clientId', type: 'int'  },
  {name: 'name'    , type: 'string'},
  {name: 'phone'   , type: 'string'},
  {name: 'website' , type: 'string'},
  {name: 'status'  , type: 'string'},
  {name: 'clientSince' , type: 'date', dateFormat: 'Y-m-d H:i'}
],
validators:{
  name:[
    { type:'presence'}
  ],
  website:[
    { type:'presence', allowEmpty:true},
    { type:'length',  min: 5, max:250 }
  ]
}
});
```

```js
//Step 1
var myclient = Ext.create('Myapp.model.Client',{
    clientId  : '10001',
    name  : 'Acme corp',
    phone: '+52-01-55-4444-3210',
    website: 'www.acmecorp.com',
    status: 'Active',
    clientSince: '2010-01-01 14:35'
});

if   (myclient.isValid()){  //Step 2
  console.log("myclient model is correct");
}

console.log(myclient);
console.log("My client's name is = " + myclient.data.name);
console.log("My client's website is = " + myclient.data.website);
// SET methods   //Step 3
myclient.set('name','');
myclient.set('website','');
if   (myclient.isValid()){//Step 4
  console.log("myclient model is correct");
} else {
//Step 5
  console.log("myclient model has errors");
  var errors = myclient.validate();
  errors.each(function(error){
    console.log(error.field,error.message);
  });
}
```

> **NOTA:**
> 

![04-05](images/04-05.png)

### Tipos de campos personalizados

```js
Ext.define('Myapp.fields.Status',{
    extend: 'Ext.data.field.String',  //Step 1
    alias: 'data.field.status',//Step 2
    validators: {//Step 3
        type: 'inclusion',
        list: [ 'Active', 'Inactive'],
        message: 'Is not a valid status value, please select the proper options[Active, Inactive]'
    }
});
```

```js
Ext.define('Myapp.model.Client',{
extend:'Ext.data.Model',
idProperty:'clientId ',
fields:[
  {name: 'clientId', type: 'int'  },
  {name: 'name'    , type: 'string'},
  {name: 'phone'   , type: 'string'},
  {name: 'website' , type: 'string'},
  {name: 'status'  , type: 'status'}, //Using custom field
  {name: 'clientSince' , type: 'date', dateFormat: 'Y-m-d H:i'}
],
validators:{
  ...
}
});
```

```js
var myclient = Ext.create('Myapp.model.Client',{
  clientId: '10001',
  name: 'Acme corp',
  phone: '+52-01-55-4444-3210',
  website: 'www.acmecorp.com',
  status: 'Active',
  clientSince: '2010-01-01 14:35'
});
if(myclient.isValid()){
  console.log("myclient model is correct");
}
// SET methods
myclient.set('status','No longer client');
if(myclient.isValid()){
  console.log("myclient model is correct");
} else {
  console.log("myclient model has errors");
  var errors = myclient.validate();
  errors.each(function(error){
    console.log(error.field,error.message);
  });
}
```

> **TIP:**
> 

![04-06](images/04-06.png)

### Relaciones

#### ASOCIACIONES ONE-TO-MANY 

```js
Ext.define('Myapp.model.Client',{
  extend:'Ext.data.Model',  // step 1
  requires: ['Myapp.model.Employee'],
  idProperty:'id ',
  fields:[....  ],
  hasMany:{
    model:'Myapp.model.Employee',
    name:'employees',
    associationKey: 'employees'
  }
});
```

```js
Ext.define('Myapp.model.Employee',{
  extend:'Ext.data.Model',
  idProperty:'id ',
  fields:[
    {name: 'id', type: 'int' },
    {name: 'clientid'  , type: 'int'},
    {name: 'name'      , type: 'string'},
    {name: 'phone'     , type: 'string'},
    {name: 'email'     , type: 'string'},
    {name: 'gender'    , type: 'string'}
  ]
});
```

```js
yee. In order to test our relationship, we need to create an HTML file importing the Ext JS library and our two models. Then, we can test our models as follows:

var myclient = Ext.create('Myapp.model.ClientWithContacts',{
  id: 10001,
  name: 'Acme corp',
  phone: '+52-01-55-4444-3210',
  website: 'www.acmecorp.com',
  status: 'Active',
  clientSince: '2010-01-01 14:35'
});
//Step 2
myclient.employees().add(
{
  id:101, clientId:10001, name:'Juan Perez', phone:'+52-05-2222-333', email:'juan@test.com', gender:'male'},
{
  id:102, clientId:10001, name:'Sonia Sanchez', phone:'+52-05-1111-444', email:'sonia@test.com',gender:'female'}
);
//Step 3
myclient.employees().each(function(record){
  console.log(record.get('name') + ' - ' + record.get('email') );
});
```


#### ASOCIACIONES One-to-one

```js
Ext.define('Myapp.model.Contract',{
  extend:'Ext.data.Model',
  idProperty:'id ',
  fields:[
    {name: 'id', type: 'int' },
    {name: 'contractId', type: 'string'},
    {name: 'documentType', type: 'string'}
  ]
});
As you can see this is a plain model. Now on the Customer class we will define it as follows:

Ext.define('Myapp.model.Customer',{
  extend:'Ext.data.Model',
requires: ['Myapp.model.Contract'],
  idProperty:'id ',
fields:[
  {name: 'id', type: 'int'},
  {name: 'name'    , type: 'string'},
  {name: 'phone'   , type: 'string'},
  {name: 'website' , type: 'string'},
  {name: 'status'  , type: 'string'},
  {name: 'clientSince' , type: 'date', dateFormat: 'Y-m-d H:i'},
  {name: 'contractInfo' , reference: 'Contract', unique:true}
  ]
});
```

```js
var myclient = Ext.create('Myapp.model.Customer',{
  id: 10001,
  name: 'Acme corp',
  phone: '+52-01-55-4444-3210',
  website: 'www.acmecorp.com',
  status: 'Active',
  clientSince: '2010-01-01 14:35',
  contractInfo:{
    id:444,
    contractId:'ct-001-444',
    documentType:'PDF'
  }
});
```

![04-07](images/04-07.png)

![04-08](images/04-08.png)


## Trabajando con store

```js
Ext.define('MyApp.store.Customers',{
  extend : 'Ext.data.Store',        //Step 1
  model  : 'Myapp.model.Customer'  //Step 2
});
```

```js
var store = Ext.create("MyApp.store.Customers");
//counting the elements in the store
console.log(store.count());
```

### Añadiendo nuevos elementos

```js
//Step 1 (define /create new model instance)
var mynewcustomer = Ext.create('Myapp.model.Customer',{
  id: 10001,
  name: 'Acme corp',
  phone: '+52-01-55-4444-3210',
  website : 'www.acmecorp.com',
  status: 'Active',
  clientSince: '2010-01-01 14:35',
  contractInfo:{
    id:444,
    contractId:'ct-001-444',
    documentType:'PDF'
  }
});
store.add(mynewcustomer); //Step 2
console.log("Records in store:" + store.getCount() );
```

```js
//Method 2 for add Records
  store.add({
    id: 10002,
    name: 'Candy Store LTD',
    phone: '+52-01-66-3333-3895',
    website : 'www.candyworld.com',
    status: 'Active',
    clientSince: '2011-01-01 14:35',
    contractInfo:{
      id:9998,
      contractId:'ct-001-9998',
      documentType:'DOCX'
    }
  });
  console.log("Records in store:" + store.getCount());
```

```js
// Method 3 for add multiple records
  var mynewcustomer = Ext.create('Myapp.model.Customer', { ...});
  var mynewcustomerb = Ext.create('Myapp.model.Customer', {
  ...});
  store.add([mynewcustomer, mynewcustomerb]);
  console.log("Records in store:" + store.getCount());
```

### Recorrer los records/models en el store.

```js
store.each(function(record, index){
  console.log(index, record.get("name"));
});
```

### Recuperar los records en el store

#### POR INDEX POSITION

```js
var modelTest = store.getAt(2);
console.log(modelTest.get("name"));
```


#### PRIMER Y ÚLTIMO REGISTRO

```js
var first = store.first();
var last = store.last();
console.log(first.get("name"), last.get("name"));
```

#### POR RANGO

```js
var list = store.getRange(1,3);

Ext.each(list,function(record,index){
  console.log(index,record.get("name"));
});
```

#### POR ID

```js
var record = store.getById(10001);
console.log(modelTest.get("name"));
```

### Eliminación de registros

```js
store.remove(record);
store.each(function(record,index){
  console.log(index,record.get("name"));
});
```

```js
store.remove([first,last]);
store.each(function(record,index){
  console.log(record.get("name"));
});
```

```js
store.removeAt(2);
store.each(function(record,index){
  console.log(index,record.get("name"));
});
```

```js
store.removeAll();
console.log("Records:",store.count());
```

## Recuperando datos remotos

### Ajax proxy

```js
Ext.define('Myapp.store.customers.Customers',{
  extend:'Ext.data.Store',
  model: 'Myapp.model.Customer',
  proxy:{
    type:'ajax',
    url: 'serverside/customers.php',
    reader: {
      type:'json',
      rootProperty:'records'
    }
  }
});
```

```js
//Step 1
  var store = Ext.create("Myapp.store.customers.Customers");
  //Step 2
  store.load(function(records, operation, success) {

    console.log('loaded records');//Step 3
    Ext.each(records, function(record, index, records){
      console.log( record.get("name")  + '  - '  + record.data.contractInfo.contractId );
    });
  });
```

```js
{
  "success":true,
  "id":"id",
  "records":[
    {
      "id": 10001,
      "name": "Acme corp2",
      "phone": "+52-01-55-4444-3210",
      "website": "www.acmecorp.com",
      "status": "Active",
      "clientSince": "2010-01-01 14:35",
      "contractInfo":{
        "id":444,
        "contractId":"ct-001-444",
        "documentType":"PDF"
      }
    },{
      "id": 10002,
      "name": "Candy Store LTD",
      "phone": "+52-01-66-3333-3895",
      "website": "www.candyworld.com",
      "status": "Active",
      "clientSince": "2011-01-01 14:35",
      "contractInfo":{
        "id":9998,
        "contractId":"ct-001-9998",
        "documentType":"DOCX"
      }
    }
  ]
}
```

### Readers

```js
reader: {
  type:'json',
  rootProperty:'records'
}
```

```js
{
  "success" :"true",
  "id":"id",
  "output":{
    "appRecords":[{ our data .... }],
    "customerRecords":[{ our data .... }]
  }
}
```

```js
reader: {
  type:'json',
  rootProperty:'output.customerRecords'
}
```

#### XML READER(LECTOR XML)

```js
proxy:{
    type:'ajax',
    url: 'serverside/customers.xml',
    reader: {
      type: 'xml',
      rootProperty: 'data',
      record:'customer',
      totalProperty: 'total',
      successProperty: 'success'
    }
  }
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<data>
  <success>true</success>
  <total>2</total>
  <customer>
    <id>10001</id>
    <name>Acme corp2</name>
    <phone>+52-01-55-4444-3210</phone>
    <website>www.acmecorp.com</website>
    <status>Active</status>
    <clientSince>2010-01-01 14:35</clientSince>
    <contractInfo>
      <id>444</id>
      <contractId>ct-001-444</contractId>
      <documentType>PDF</documentType>
    </contractInfo>
  </customer>
  <customer>
    <id>10002</id>
    <name>Candy Store LTD</name>
    <phone>+52-01-66-3333-3895</phone>
    <website>www.candyworld.com</website>
    <status>Active</status>
    <clientSince>2011-01-01 14:35</clientSince>
    <contractInfo>
      <id>9998</id>
      <contractId>ct-001-9998</contractId>
      <documentType>DOCX</documentType>
    </contractInfo>
  </customer>
</data>
```

![04-09](images/04-09.png)


## Enviando datos

```js
Ext.define('Myapp.store.customers.CustomersSending',{
  extend:'Ext.data.Store',
  model: 'Myapp.model.Customer',
  autoLoad:false,
  autoSync:true,
  proxy:{
    type:'ajax',
    url: 'serverside/customers.json',
    api: {
      read    : 'serverside/customers.json',
      create  : 'serverside/process.php?action=new',
      update  : 'serverside/process.php?action=update',
      destroy : 'serverside/process.php?action=destroy'
    },
    reader: {
    ()type:'json',
      rootProperty:'records'
          },
    writer:{
      type:'json',
      encode:true,
      rootProperty:'paramProcess',
      allowSingle:false,
      writeAllFields:true,
      root:'records'
    },
    actionMethods:{
      create: 'POST',
      read: 'GET',
      update: 'POST',
      destroy: 'POST'
    }
  }
});
```

> **NOTA:**
> 

```html
<!doctype html>
<html>
<head>
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta charset="utf-8">
<title>Extjs - Sending 01</title>
<link rel="stylesheet" type="text/css" href="../ext-5.1.1/build/packages/ext-theme-neptune/build/resources/ext-theme-neptune-all.css">
<script src="../ext-5.1.1/build/ext-all.js"></script>
<script src="../ext-5.1.1/build/packages/ext-theme-neptune/build/ext-theme-neptune.js"></script>
<script type ="text/javascript" src="sending_01.js"></script>
</head>
<body style="padding:10px;"></body>
</html>
```

```js
Ext.Loader.setConfig({
   enabled: true,
  paths:{ Myapp:'appcode' }
});
Ext.require([
  'Ext.data.*',
  'Myapp.model.Contract',
  'Myapp.model.Customer',
  'Myapp.store.customers.CustomersSending'
]);
Ext.onReady(function(){

var store = Ext.create("Myapp.store.customers.CustomersSending"); //Step 1
  store.load({ // Step 2 load  Store in order to get all records
    scope: this,
    callback: function(records, operation, success) {
      console.log('loaded records');
      Ext.each(records, function(record, index, records){
        console.log( record.get("name")  + '  - '  + record.data.contractInfo.contractId );
      });
      var test=11;
      console.log('Start adding model / record...!');
      // step 3 Add a record
      var mynewCustomer = Ext.create('Myapp.model.Customer',{
        clientId  : '10003',
        name: 'American Notebooks Corp',
        phone: '+52-01-55-3333-2200',
        website   : 'www.notebooksdemo.com',
        status    : 'Active',
        clientSince: '2015-06-01 10:35',
        contractInfo:{
          "id":99990,
          "contractId":"ct-00301-99990",
          "documentType":"DOC"
        }
      });
      store.add(mynewCustomer);

      // step 4 update a record

      console.log('Updating model / record...!');
      var updateCustomerModel = store.getAt(0);
      updateCustomerModel.beginEdit();
      updateCustomerModel.set("website","www.acmecorpusa.com");
      updateCustomerModel.set("phone","+52-01-33-9999-3000");
      updateCustomerModel.endEdit();

      // step 5 delete  a record
      console.log('deleting a model / record ...!');

      var deleteCustomerModel = store.getAt(1);
      store.remove(deleteCustomerModel);

    }
  });
});
```

![04-10](images/04-10.png)

## Resumen



