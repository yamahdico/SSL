Standard DV SSL

Commercial Wildcard SSL



Download openssl in windows:
https://slproweb.com/products/Win32OpenSSL.html


Example: openssl pkcs12 -in yourfile.pfx -out outputfile.pem ***-legacy -provider-path "C:\Program Files\OpenSSL-Win64\bin"***

Execute the below commands to extract the certificates:

1. Extract the RSA Key from the PFX file:

$ openssl pkcs12 -in <PFX_file> -nocerts -nodes -out nutanix-key-pfx.pem

2. Extract the Public Certificate from the PFX file:

$ openssl pkcs12 -in <PFX_file> -clcerts -nokeys -out nutanix-cert-pfx.pem

3. Extract the CA Chain from the PFX file:

$ openssl pkcs12 -in <PFX_file> -cacerts -nokeys -chain -out ca-pfx.pem

4. Convert the RSA Key from PFX format to PEM:

$ openssl rsa -in nutanix-key-pfx.pem -out nutanix-key.pem

5. Convert the x509 Public Certificate and CA Chain from PFX to PEM format:

$ openssl x509 -in nutanix-cert-pfx.pem -out nutanix-cert.pem

$ openssl x509 -in ca-pfx.pem -out ca.pem

Download nutanix-key.pem, nutanix-cert.pem and ca.pem from the Linux system to a local desktop.
After following the steps above, the needed certificates and keys will be generated in a preset working directory, and it can be used as follows.

-    Private Key Type: RSA 2048-bit
-    Private Key: nutanix-key.pem
-    Public Certificate: nutanix-cert.pem
-    CA Certificate/Chain: ca.pem

openssl pkcs12 -in filename.pfx -nocerts -nodes -out clientcert.key -legacy -provider-path "C:\Program Files\OpenSSL-Win64\bin
openssl pkcs12 -in filename.pfx -clcerts -nokeys -out clientcert.cert -legacy -provider-path "C:\Program Files\OpenSSL-Win64\bin
openssl pkcs12 -in filename.pfx -cacerts -nokeys -chain -out cacerts.ca -legacy -provider-path "C:\Program Files\OpenSSL-Win64\bin


ca-bundle.crt:

openssl pkcs12 -in filename.pfx -nokeys -out fullchain.pem -legacy -provider-path "C:\Program Files\OpenSSL-Win64\bin"                                                                                                                                       


- openssl pkcs12 -in filename.pfx -nocerts -nodes | sed -ne '/-BEGIN PRIVATE KEY-/,/-END PRIVATE KEY-/p' > clientcert.key -legacy -provider-path "C:\Program Files\OpenSSL-Win64\bin
- openssl pkcs12 -in filename.pfx -clcerts -nokeys | sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' > clientcert.cert -legacy -provider-path "C:\Program Files\OpenSSL-Win64\bin
- openssl pkcs12 -in filename.pfx -cacerts -nokeys -chain | sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' > cacerts.ca -legacy -provider-path "C:\Program Files\OpenSSL-Win64\bin
