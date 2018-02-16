# Generate the crypto stuff

1. Run `generate-crypto-stuff` with no arguments. 
2. When it asks you for any password or passphrase, use "test". 
3. When it asks for information about your organization, department, etc, use
   "ca", "client", "server" for everything, accordingly with which step you're
   on.

# Install the server-side part in nginx

1. In your nginx config file, uncomment the "SSL server" section.
2. The template should have `ssl_certificate` and `ssl_certificate_key`. Set
   these to the paths to `server.crt` and `server.key`.
3. Add `ssl_client_certificate /path/to/ca.crt` and `ssl_verify_client on`
4. Restart nginx.

# Install the client cert in your OS/browser

## Chrome on Mac

1. Open "Keychain Access".
2. "File > Import Items".
3. Choose `client.p12`.
4. It will ask you for the passphrase. This should be `test` if you followed the
   instructions above.
5. You should now see "client" under "login/My Certificates".

# Test it

## Chrome on Mac

1. Navigate to https://localhost (you may need a port if you're not using the
   default of 443).
2. You should get a popup asking you which certificate to use.
