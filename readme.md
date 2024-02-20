# Export complete keycloak realm rs-platform

```shell
docker exec -it rentsoft_ms_user_keycloak /opt/jboss/keycloak/bin/standalone.sh \
-Djboss.socket.binding.port-offset=100 -Dkeycloak.migration.action=export \
-Dkeycloak.migration.provider=singleFile \
-Dkeycloak.migration.realmName=rs-platform \
-Dkeycloak.migration.usersExportStrategy=REALM_FILE \
-Dkeycloak.migration.file=/tmp/keycloak/rs_platform_realm.json
```

# Connect to gke cluster
```shell
gcloud container clusters get-credentials rs-ms-user-a --region europe-west3 --project x0-marketing
```

# Copy from GKE stage
```shell
kubectl cp default/rs-ms-user-69c5fd9459-5kpfp:/tmp/rs_platform_realm.json -c rs-ms-user ./rs_platform_realm_prod.json
```