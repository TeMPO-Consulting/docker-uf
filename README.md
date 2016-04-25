# Maintainer
    vincent.greiner@tempo-consulting.fr

# Build

    bash init
    
    will build:
        tempo/ufbuntu:10.04, core ubuntu 10.04 image
        tempo/ufbuntu:10.04, uf image
        piotrdomagalski/postgres:8.4, postgres 8.4 image
        
# Run

    bash run container_name host_unifield_workdir
    
# Access

    user docker
    docker user password: 'docker'
    root password: 'unifield'
    psql user: 'docker'
    psql docker user password: 'docker'
    
    OpenERP port: 8061
        to change port, edit run script and change forwarded port
            -p your_port:8061
    
    inside your unifield docker, for Postgres connections, please use
        'ufpg' for host
        psql -h ufpg -l
        
    docker start container_name
    docker attach container_name
    
    or you can docker exec any command you like

