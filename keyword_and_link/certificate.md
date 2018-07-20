
https://manuals.setasign.com/setapdf-signer-manual/timestamp-modules/
http://php.net/manual/en/function.openssl-sign.php

http://sk-eid.github.io/dds-documentation/
https://github.com/tractis/webservices-clients
1. TSA server: https://d-mueller.de/blog/dealing-with-trusted-timestamps-in-php-rfc-3161/
2. https://www.digistamp.com/technical/how-a-digital-time-stamp-works/

1. https://github.com/jan-zajic/tsa-server

1. https://stackoverflow.com/questions/tagged/trusted-timestamp?page=3&sort=newest&pagesize=15
2. https://stackoverflow.com/questions/13660901/pkcs7-with-timestamp
3. https://stackoverflow.com/questions/tagged/trusted-timestamp?page=5&sort=newest&pagesize=15
3. Trusted timestamp
4. https://helpx.adobe.com/acrobat/using/validating-digital-signatures.html
5. https://www.globalsign.com/en/blog/what-is-timestamping-how-does-it-work/
1. https://www.kryptokoder.com/signwithext.html#TimeStamping

5. https://www.adobe.com/devnet-docs/acrobatetk/tools/DigSigDC/Acrobat_DigitalSignatures_in_PDF.pdf

https://svn.apache.org/viewvc/pdfbox/trunk/examples/src/main/java/org/apache/pdfbox/examples/signature/

## keyword
1. pkcs#7 signature php

https://www.digistamp.com/toolkitDownload.htm
http://tsatest1.digistamp.com/tsa
http://tsatest2.digistamp.com/tsa
PHP RFC3161 Timestamp Toolkit
https://www.digistamp.com/technical/software-alternatives/using-php-toolkit-to-provide-timestamp-services
https://www.digistamp.com/technical/software-alternatives/using-openssl-to-request-timestamps/

https://www.digistamp.com/technical/technical-details-about-integrating-digistamp-tsas

Digitally Sign and timestamp a PDF in java: trusted timestamp authority.
digital certificate

http://supporttest.digistamp.com/account/Website

Thank you for registering with DigiStamp

You can login, with your email address and password you specified, at:
supporttest.digistamp.com/account And use the test TSAs:

tsatest1.digistamp.com/tsa
tsatest2.digistamp.com/tsa
Your account number and a link to download the toolkits will be e-mailed to you (ducxinh201@gmail.com) shortly. 
(e-mail will be from: support@DigiStamp.com)
The toolkit software will require:
Your assigned account number
The password you just entered
If you have any suggestions or problems, then use our feedback form on this WEB site or write to support@digistamp.com.



## Tạo file xác thực
1. To create self-signed signature:
```
openssl req -x509 -nodes -days 365000 -newkey rsa:1024 -keyout tcpdf.crt -out tcpdf.crt
```

2. To export crt to p12: `openssl pkcs12 -export -in tcpdf.crt -out tcpdf.p12`
    Or
2. To export crt to p12: `openssl pkcs12 -export -in tcpdf.crt -out tcpdf.pfx`

3. To convert pfx certificate to pem: `openssl pkcs12 -in tcpdf.pfx -out tcpdf.crt -nodes`

4. set certificate file: `$certificate = 'file://data/cert/tcpdf.crt';`


## Thư viện
1. setasign/fpdi-tcpdf (Thư viện triển khai)
2. https://github.com/hablutzel1/phpcmstimestamper
3. https://tcpdf.org/docs/srcdoc/


https://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/

2. tecnickcom/tcpdf
3. http://www.fpdf.org/: http://www.fpdf.org/en/tutorial/index.php
3. App view chứng thực: Reader DC: https://helpx.adobe.com/acrobat/kb/install-reader-dc-mac-os.html
4. https://tcpdf.org/examples/example_052/

1. fpdf: Old
1. setasign/fpdi: New
2. https://github.com/tecnickcom/TCPDF: new

## Timestamp
1. https://www.setasign.com/products/setapdf-signer/demos/

## Document
1. https://www.setasign.com/



## Example:
1. https://www.setasign.com/products/setapdf-signer/demos/simple-usage-demo/

## Thư viện code
1. setasign/setapdf-signer-addon-cosign
2. setasign/setapdf-signer-addon-quovadis
3. setasign/setapdf-signer-addon-swisscomais

5. composer require setasign/fpdi ^2.0
4. composer require tecnickcom/tcpdf ^6.2

## Tham Khảo
1. https://www.setasign.com/products/setapdf-signer/demos/sign-encrypted-pdf-documents/#p-596
2. https://tcpdf.org/examples/example_052/
3. https://stackoverflow.com/questions/16100109/tcpdf-adding-digital-signature-to-the-created-pdf

## Check about PDF
    - File-> property: title, author, subject, keyword,

## timestamp tcpdf
    - getDocCreationTimestamp()
    - setDocCreationTimestamp(time)
    - setDocModificationTimestamp(time)
    - getDocModificationTimestamp()

## Trust list
    + http://www.fpdf.org/
    + https://helpx.adobe.com/acrobat/kb/approved-trust-list2.html
    + https://helpx.adobe.com/acrobat/kb/approved-trust-list1.html
    + https://helpx.adobe.com/acrobat/using/trusted-identities.html
    + http://www.entrust.net/knowledge-base/technote.cfm?tn=70599
    + https://helpx.adobe.com/sign/kb/digital-certificate-providers.html

```
$pdf->Text(10, 10, 'ID: Kpd133gh');
$pdf->Image(public_path('/approved.png'), 10, 10, 12,12);
$pdf->Image(public_path('/logo.png'), $pdf->GetPageWidth() - 30, $pdf->GetPageHeight() - 30, 16,16);
```

- chứng thực lên file luôn,: Signed and all signatures are valid

- Authenticate Company (API CER001, 002, 003, 004): ?
-- Authenticate PDF file  (API PDF001, 002): ?

- https://tcpdf.org/examples/example_052/

```
/*
NOTES:
 - To create self-signed signature: openssl req -x509 -nodes -days 365000 -newkey rsa:1024 -keyout tcpdf.crt -out tcpdf.crt
 - To export crt to p12: openssl pkcs12 -export -in tcpdf.crt -out tcpdf.p12
 - To convert pfx certificate to pem: openssl pkcs12 -in tcpdf.pfx -out tcpdf.crt -nodes
*/

// set certificate file
$certificate = 'file://data/cert/tcpdf.crt';
```

- https://github.com/tecnickcom/tc-lib-pdf
    + https://tcpdf.org/examples/example_052/
    + https://tcpdf.org/examples/
- https://www.qoppa.com/pdfstudio/download/
- https://www.youtube.com/watch?v=klULOB8lerU

- Case 2. Chữ ký điện tử + timestamp

- mọi người cho mình hỏi cái này chút:
cái chữ ký là mình tạo ra 1 lần thôi đúng ko (tạo bằng lênh `openssl`), mình sẽ lưu chữ ký đó vào source code của mình
rồi mỗi lần upload cái file pdf nào lên thì add cái chữ ký đó vào file pdf phải ko nhỉ?

- https://docs.google.com/spreadsheets/u/1/d/1zYnuceF8aCsieVKiAnmCipXgUpX73c9k-nRzoQQB_0U/edit#gid=750013968

- PDFtimestamp có phải là encrypt cái time lúc signer tạo hả ?
Auth PDFtimestamp như thế nào?
Cái add template pdf là mình tạo sẵn cái form để các thông tin user cần fill vô (giống như file vô form xin việc mấy trang online) rồi xuất ra file pdf kèm signature  ?



- Tuan
`libraries:` mình dùng 2 thư viện
1. `setasign/fpdi-tcpdf`
2. `tecnickcom/tcpdf`
cách tạo chữ ký: mình đã tạo sẵn 1 chữ ký và lưu vào trong source
open terminal chạy lệnh:
1. tạo file `crt`: `openssl req -x509 -nodes -days 365000 -newkey rsa:1024 -keyout tcpdf.crt -out tcpdf.crt`
2. set password: `openssl pkcs12 -export -in tcpdf.crt -out tcpdf.p12`
3. convert qua file pem nếu muốn :D: `openssl pkcs12 -in tcpdf.p12 -out tcpdf.pem -nodes`


https://github.com/Zizaco/entrust