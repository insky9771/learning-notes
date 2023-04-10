openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout odesvtdb.key -out odesvtdb.crt -subj "/CN=apim-tls"

openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout prodprimedb.key -out prodprimedb.crt -subj "/CN=**"

openssl req -newkey rsa:2048 -new -out test.csr -keyout test.key


// CRT => PFX  pkcs12 -export -inkey test1.key -in test.crt -out test.pfx 
// PFX => JKS  keytool -importkeystore -srckeystore test.pfx -destkeystore test.jks -srcstoretype PKCS12 -deststoretype JKS

kubectl create secret tls aro-tls --key=aro.key --cert=aro.crt
