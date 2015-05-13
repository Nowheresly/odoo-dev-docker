# odoo-dev-docker

## build the data container
`docker build -f DockerfileData -t odoodata .`

## run the data container
docker run --name odoodata <id>

## run the postgresql container
docker run -p 5432:5432 --volumes-from odoodata -d -e \
POSTGRES_USER=odoo -e POSTGRES_PASSWORD=odoo --name dbodoodata \
-v /c/Users/srichard/docker/odoorun/postgresql/logs:/var/log/postgresql \
postgres

## build the odoo dev container
docker build -f DockerfileOdoo -t odoodev .

## run the odoo dev container
docker run -p 8069:8069 --name odoodev --link dbodoodata:db \
-v /c/Users/srichard/odoo-dev:/root/odoo-dev

## start a bash and start the server
docker exec -i -t odoodev bash
cd odoo-dev
./odoo.py
