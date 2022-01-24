

## Migrate to kubernetes lychee
`kubectl cp ~/backup/haakma_verbouw.sql mariadb-0:/tmp/. -n lychee`

`kubectl exec -it pod/mariadb-0 bash -n lychee`

`mysql -U root lychee -p < /tmp/backup.sql`