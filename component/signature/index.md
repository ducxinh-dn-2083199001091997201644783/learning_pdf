1. to create self-signed signature: 
    + `openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout tcpdf.crt -out tcpdf.crt`
    + syntax:
    ```
    openssl req -nodes -newkey rsa:2048 -keyout example.key -out example.csr 
    -subj "/C=VN/ST=London/L=London/O=Global Security/OU=IT Department/CN=example.com"
    ```
    ```
    openssl req -new -nodes -sha256 -newkey rsa:2048 -keyout example.com.key -out example.com.csr -subj "/emailAddress=ducxinh201@gmail.com/CN=example.com/O=MyOrganization/OU=MyUnit/C=VN/ST=DanangST/L=DanangL"
    ```

    + Offical
     `openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout tcpdf.crt -out tcpdf.crt -subj "/emailAddress=ducxinh201@gmail.com/C=VN/ST=DanangSt/L=DanangL/O=Global Security/OU=IT Department/CN=ducxinh.com"`

2. View
    `openssl req -text -noout -verify -in example.com.csr`
2. To export crt to p12: 
    + `openssl pkcs12 -export -in tcpdf.crt -out tcpdf.p12`
3. To convert pfx certificate to pem: 
    + `openssl pkcs12 -in <cert.pfx> -out <cert.crt> -nodes`