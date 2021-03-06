# Wordpress

## Deploying Wordpress

### Using helm

`helm install . --generate-name -n haakma-org --create-namespace`

### Check deployment
```bash
kubens haakma-org
kubeclt get all
```

### Remove deployment
`kubbectl delete namespace haakma-org`
## Migrate to kubernetes deployment
To migrate you workdpress site to kubernetes you need to migrate 2 components:
- the `wp-content` data
- the database data
### Copy the content in the container
The `wp-content` directory is located in `/bitnami/wordpress` in the container.

`kubectl cp backup/haakma.org/backup.tar #pod-name#:/tmp/.`

Then exec into the container

`kubectl exec -it pod/pod-name bash`

Untar the file

```bash
cd /tmp
tar -xvf /tmp/backup.tar
```

Move the files into the wordpress dir.

```bash
mv /bitnami/wordpress/wp-content /bitnami/wordpress/wp-content_backup
mv /tmp/wp-content /bitnami/wordpress/
```

### Load the database in the container
Copy the backup to the mysql docker.

`kubectl cp backup/haakma.org/backup.sql #pod-name#:/tmp/.`

Enter the docker container

`kubectl exec -it pod/pod-name bash`

Load the database:

`mysql -u database_user -p database < /tmp/backup.sql`





