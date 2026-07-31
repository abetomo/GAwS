

# GAwS
Un fork de [aws-apps-scripts](https://github.com/smithy545/aws-apps-scripts).
Un script para llamar a la API de AWS desde Google Apps Script.

## Cómo usarlo:

1. Crea un nuevo proyecto en Google Apps Script.
2. Copia y pega aws.js en su propio archivo dentro de tu proyecto y guárdalo.
3. Abre un nuevo archivo y configura la variable AWS con AWS.init.
4. Usa el método para cada servicio.

## Ejemplo:
### EC2

```javascript
function myFunction() {
  AWS.init('MY_ACCESS_KEY', 'MY_SECRET_KEY');
  console.log(AWS.ec2(
    'us-east-1', // region
    'DescribeInstances', // action
    {"Version":"2015-10-01"} // params
  ));
}
```

### S3
#### Subir objeto
```javascript
function myFunction() {
  AWS.init('MY_ACCESS_KEY', 'MY_SECRET_KEY');
  console.log(AWS.s3(
    'us-west-2', // region
    'bucket', // bucket
    'key', // key
    'PUT', // method
    '{"key":"value"}' // payload
  ));
}
```

#### Obtener objeto
```javascript
function myFunction() {
  AWS.init('MY_ACCESS_KEY', 'MY_SECRET_KEY');
  res = AWS.s3(
    'us-west-2', // region
    'bucket', // bucket
    'key', // key
    'GET' // method
  );
  console.log(res.getContentText());
}
```

### Lambda
#### Síncrono
```javascript
function myFunction() {
  AWS.init('MY_ACCESS_KEY', 'MY_SECRET_KEY');
  console.log(AWS.lambdaInvoke(
    'us-west-2', // region
    'functionName', // functionName
    '{"key":"value"}' // payload
  ));
}
```

#### Asíncrono
```javascript
function myFunction() {
  AWS.init('MY_ACCESS_KEY', 'MY_SECRET_KEY');
  console.log(AWS.lambdaInvokeAsync(
    'us-west-2', // region
    'functionName', // functionName
    '{"key":"value"}' // payload
  ));
}
```
