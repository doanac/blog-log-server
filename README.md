Set up a "blog log server" to complement the "blog log agent"

## Step 1: Create TLS certs
You'll need to create TLS certs for the DNS name of your blog log server. In
this example, we'll use `example.com`. You'll need access to the PKI certs
set up by the factory administrator. This directory will have files like:

 * factory_ca.key
 * sign_tls_csr
 * factory_ca.pem
 * local-ca.pem

You can create the TLS certs with a command like:
```
 $ ./create_new_server </mnt/example.com-pki> example.com
```

This will create 3 files:

 * ./certs/tls.key
 * ./certs/tls.pem
 * ./certs/ca-chain.pem

## Step 2: Run the server

```
 $ docker-compose up
```

Start creating events from the blog log agent and watch for nginx logs like
```
 "POST / HTTP/1.1" 200 12 "-" "Go-http-client/1.1" "-"
```
