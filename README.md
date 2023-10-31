# yaml-service-hpa-ingress



Generate a Self-Signed Certificate:
$ openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout tls.key -out tls.crt

Create a Kubernetes Secret:
$ kubectl create secret tls test-tls-secret --cert=tls.crt --key=tls.key
You can manually create secret and apply the fields. You need to base64 encode your certificate

base64 encode your certificate and key:
$ cat tls.crt | base64
$ cat tls.key | base64


Make sure that the metrics-server is running in your cluster to collect the metrics. Othervise hpa won't work.

Make sure that you have valid resource requests and limits is set inside of the pod section.    