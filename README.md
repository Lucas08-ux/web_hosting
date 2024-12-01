# Web Hosting

## Hosting y dominio de mi sitio web

En esta práctica he usado ngrok, un servicio gratuito que ofrece un dominio y hosting gratuito. Aquí dejo la url de la página oficial de ngrok:

[Visita ngrok](https://ngrok.com/)

### Cambios en el Vagrantfile

He modificado el archivo Vagrantfile que he usado en la práctica anterior y le he añadido estas líneas, que aparecen como tutorial en el sitio oficial de ngrok para que al iniciar la maquina virtual, esta se pueda ver a través del dominio gratuito que ofrece ngrok:

```
sudo apt-get install -y curl

    curl -sSL https://ngrok-agent.s3.amazonaws.com/ngrok.asc \
	| sudo tee /etc/apt/trusted.gpg.d/ngrok.asc >/dev/null \
	&& echo "deb https://ngrok-agent.s3.amazonaws.com buster main" \
	| sudo tee /etc/apt/sources.list.d/ngrok.list \
	&& sudo apt update \
	&& sudo apt install ngrok

    ngrok config add-authtoken 2pX5ecjSZHMi6vnTxGuKNcQu6LU_29DTXuDmKySzCo1GAniQf
    sudo nohup ngrok http --url=funky-kingfish-legible.ngrok-free.app 443 & 
```
También creo estos dos usuarios que voy a usar más adelante:
```
    sudo sh -c "echo 'admin:$(openssl passwd -apr1 asir)' >> /etc/nginx/admin.htpasswd"

    sudo sh -c "echo 'sysadmin:$(openssl passwd -apr1 risa)' >> /etc/nginx/status.htpasswd"
```
No tengo que hacer ningún tipo de redirección de puertos ni configurar el dns, puesto que todo esto ya me lo hace el hosting gratuito de ngrok.

### Certificado de Let's Encrypt
