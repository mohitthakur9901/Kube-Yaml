# Kubernetes CSR Approval Guide

This guide provides instructions for creating and approving a Certificate Signing Request (CSR) in Kubernetes. Follow the steps below to generate a CSR, create a CSR object in Kubernetes, and retrieve a signed certificate.

## Prerequisites

- Kubernetes cluster
- `kubectl` command-line tool
- OpenSSL installed

## Step 1: Create a CSR

Generate a private key and CSR for the user. In this example, we will use "mohit" as the user.

```sh
# Generate private key
openssl genrsa -out mohit.key 2048

# Generate CSR
openssl req -new -key mohit.key -out mohit.csr -subj "/CN=mohit/O=group1"

# Convert the CSR to Base64 format
cat mohit.csr | base64 | tr -d '\n'

# After applying csr.yaml
kubectl certificate approve mohit

#Retrieve the Signed Certificate:

 kubectl get csr mohit -o jsonpath='{.status.certificate}' | base64 --decode > mohit.crt
```

Feel free to copy this into a `README.md` file in your repository!
