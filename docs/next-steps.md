# Next steps

Now that the application can be deployed into a Minikube cluster, the next steps would be to deploy the services to the cloud (AKS, EKS, etc.).
This is where more best practices can be considered:
* Scalability - deciding how many replicas of the service to configure and how many resources each should be using.
* Availability - what geo/region the services should be running in and how best to failover in case something goes wrong.
* Security - configure the networking inside the cluster and lock down the database to only be accessible by the HTTP server. Also, use a Vault to store secrets (e.g. connection string or database password).
* Monitoring and alerting - set up alerts that would trigger when something goes wrong and dashboards that can be used to investigate where the problem might be.

# Alternative solution

## Using managed infrastructure

In this example, the Postgres database was deployed alongside the server in the same cluster. Another option could be to deploy the database outside of the cluster.

The benefit would be that Terraform can be used to deploy the database and store the connection string (or password) in a Vault. The server heml configuration can link to the secret which can be pulled when the server gets deployed in the cluster.

The disadvantage with this solution is that by adding managed infrastructure, we are basically increasing the attack surface of the overall solution, therefore, security practices like adding a firewall should be considered for the database.