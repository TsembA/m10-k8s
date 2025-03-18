
Create the secret then run command ```k apply -f mongo-secret.yaml``` so secret can be referenced in Deployment configuration file
Check the secret ```k get secret```
Applay k apply -f mongo.yaml
k describe pod <NAME OF THE POD> to check pod satus

Service configuration File 
kind: "Service"
metadate/name : "Random name"
selector: "to connect to the pod trough label"
ports
    port: Service port
    targetPort: containerPort of service
    