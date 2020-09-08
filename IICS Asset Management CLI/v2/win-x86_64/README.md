You can access code signing certificate [here](https://github.com/InformaticaCloudApplicationIntegration/Tools/tree/master/IICS%20Asset%20Management%20CLI/certificates/)  

You can validate the integrity of digitally signed binaries using any available tools, such as OpenSSL.  

For instance, 

If you have to verify the package authentication and confirm the code security, enter the following OpenSSL commands:  
openssl base64 -d -in <signature> -out /tmp/sign.sha256  
openssl dgst -sha256 -verify <(openssl x509 -in <cert> -pubkey -noout) -signature /tmp/sign.sha256 <file>

Where:  
  `<signature>` is the file containing the signature in Base64,  
  <cert> is the code signing certificate, and  
  <file> is the file to verify.  
     
Based on verification process, OpenSSL displays a success or error message to validate if the code is genuine or not.
