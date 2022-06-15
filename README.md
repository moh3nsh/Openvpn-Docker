
## Get Started!


1. cd openvpn
```
2. Change the `.env` environment-file to your needs
```
# Environment File for OpenVPN Server

# Hostname on which your server is reachable
HOSTNAME=myvpn.net

# Protocol to use by OpenVPN: TCP/UDP
PROTO=udp

# The port which should be exposed on the docker host
PUBLIC_PORT=1194
```
3. Install the OpenVPN Server
```
./OpenVPN-Install.sh
```
4. Start the OpenVPN Server
```
docker-compose up -d
```

## Create new OpenVPN Client
The creation of new clients and configuration is also script based.
```
# Create client without private key passphrase
./Create-Client-Conf.sh myvpn nopass

# Create client with private key passphrase
./Create-Client-Conf.sh myvpn
```
The client will get registered in the server and a myvpn.ovpn configuration file will be saved to `client-confs/myvpn.ovpn`

To get the client configuration file of a previously created client:
```
./Get-Client-Conf.sh myvpn
```

## Revoke Client
You may want to revoke clients from accessing your server.
```
./Revoke-Client-Conf.sh myvpn
```
This will revoke the client's certificate and remove all files and configuration from your server

