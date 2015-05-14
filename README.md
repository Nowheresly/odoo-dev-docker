# odoo-dev-docker

## build the data container
`docker build -f DockerfileData -t odoodata .`

## run the data container
`docker run --name odoodata <id>`

## build the odoo dev container
`docker build -f DockerfileOdoo -t odoodev .`

## run the odoo dev container
`docker run -p 8069:8069 --name odoodev \`
`-p 5432:5432 \`
`--volumes-from odoodata \`
``-v /c/Users/srichard/postgresql:/var/lib/postgresql \`
`-v /c/Users/srichard/odoo-dev:/home/odoo/odoo-dev`

## start a bash and start the server
`docker exec -i -t odoodev bash`
`cd odoo-dev`
`python odoo.py setup_deps`
`python odoo.py setup_pg`
`./odoo.py`
