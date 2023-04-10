openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout odesvtdb.key -out odesvtdb.crt -subj "/CN=apim-tls"

openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout prodprimedb.key -out prodprimedb.crt -subj "/CN=optimizer-prodprimedb.intranet.ibm.com"

openssl req -newkey rsa:2048 -new -out sdbxdb01.csr -keyout sdbxdb01.key


openssl req -newkey rsa:2048 -new -out kmf-kyndryl-net.csr -keyout kmf-kyndryl-net.key
openssl req -newkey rsa:2048 -new -out kmf-ocean.csr -keyout kmf-ocean.key



openssl req -newkey rsa:2048 -new -out ode-deploy.csr -keyout ode-deploy.key


openssl req -newkey rsa:2048 -new -out auth.csr -keyout auth.key


// CRT => PFX  openssl pkcs12 -export -inkey svtdb01.key -in svtdb01.crt -out svtdb01.pfx  
// PFX => JKS  keytool -importkeystore -srckeystore svtdb01.pfx -destkeystore svtdb01.jks -srcstoretype PKCS12 -deststoretype JKS


// CRT => PFX  pkcs12 -export -inkey test1.key -in test.crt -out test.pfx 
// PFX => JKS  keytool -importkeystore -srckeystore test.pfx -destkeystore test.jks -srcstoretype PKCS12 -deststoretype JKS

kubectl create secret tls aro-tls --key=aro.key --cert=aro.crt
