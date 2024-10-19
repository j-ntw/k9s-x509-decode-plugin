# plugin-demo
A demo showing how to write a plugin that can decode x509 certs.
## Setup
1. We generate a dummy tls cert and key for testing: `cert.pem` and `key.pem`
    - `openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -sha256 -days 3650 -nodes -subj "/C=XX/ST=StateName/L=CityName/O=CompanyName/OU=CompanySectionName/CN=CommonNameOrHostname"`
2. We obscure them by base64 encoding them into `cert.obs` and `key.obs` respectively. I just made up file extensions for the sake of the demo.
3. Paste each of these into `secret.yaml` and run `kubectl apply -f secret.yaml`
4. You should be able to see it in k9s secrets, and it should base64 decode into its --BEGIN CERTIFICATE-- form.
5. 