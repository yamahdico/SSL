Standard DV SSL
Commercial Wildcard SSL

openssl pkcs12 -in yourfile.pfx -out outputfile.pem ** -legacy -provider-path "C:\Program Files\OpenSSL-Win64\bin" **


https://slproweb.com/products/Win32OpenSSL.html



Execute the below commands to extract the certificates:

    Extract the RSA Key from the PFX file:

    $ openssl pkcs12 -in <PFX_file> -nocerts -nodes -out nutanix-key-pfx.pem

Extract the Public Certificate from the PFX file:

$ openssl pkcs12 -in <PFX_file> -clcerts -nokeys -out nutanix-cert-pfx.pem

Extract the CA Chain from the PFX file:

$ openssl pkcs12 -in <PFX_file> -cacerts -nokeys -chain -out ca-pfx.pem

Convert the RSA Key from PFX format to PEM:

$ openssl rsa -in nutanix-key-pfx.pem -out nutanix-key.pem

Convert the x509 Public Certificate and CA Chain from PFX to PEM format:

$ openssl x509 -in nutanix-cert-pfx.pem -out nutanix-cert.pem
$ openssl x509 -in ca-pfx.pem -out ca.pem

Download nutanix-key.pem, nutanix-cert.pem and ca.pem from the Linux system to a local desktop.
After following the steps above, the needed certificates and keys will be generated in a preset working directory, and it can be used as follows.

    Private Key Type: RSA 2048-bit
    Private Key: nutanix-key.pem
    Public Certificate: nutanix-cert.pem
    CA Certificate/Chain: ca.pem

