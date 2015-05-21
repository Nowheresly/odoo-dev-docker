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
`-v /c/Users/srichard/shareOdoo:/home/odoo/.local/share/Odoo \`
`-v /c/Users/srichard/addons/home/odoo/addons \`
`-v /c/Users/srichard/odoo-dev:/home/odoo/odoo-dev`

## start a bash and start the server
`docker exec -i -t odoodev bash`

`cd odoo-dev`

`python odoo.py setup_deps`

`python odoo.py setup_pg`

`# will create an .openerprcserver file

`python odoo.py --save`


## create the db file
`sudo mkdir -p /var/lib/postgresql/9.3/main`

`sudo chown  postgres /var/lib/postgresql/9.3/main`

`sudo chmod 700 /var/lib/postgresql/9.3/main`

`sudo su postgres -c "/usr/lib/postgresql/9.3/bin/initdb -D /var/lib/postgresql/9.3/main --encoding UTF8"`

`sudo /etc/init.d/postgresql start`

`/usr/lib/postgresql/9.3/bin/postgres -D /var/lib/postgresql/9.3/main  -c config_file=/etc/postgresql/9.3/main/postgresql.conf`
