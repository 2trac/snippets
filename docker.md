### ide 

````

# cloud9
docker run -d -v $(pwd):/workspace -p 8181:8181 sapk/cloud9 --auth username:password

# pgadmin
docker run -p 80:8888 -e 'PGADMIN_DEFAULT_EMAIL=admin@admin.com' -e 'PGADMIN_DEFAULT_PASSWORD=admin -d dpage/pgadmin4

# metabase
docker run -d -p 3000:3000 \
-v ~/metabase-data:/metabase-data \
-e "MB_DB_FILE=/metabase-data/metabase.db" \
--name metabase --network=bridge metabase/metabase

````


