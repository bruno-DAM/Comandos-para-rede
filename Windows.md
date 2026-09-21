### Comandos de rede - Windows

#### Encontrar gateway

```
# Exibe tabela de roteamento e 
netstat -r

# Exibe caminha da rede até o destino
tracert 8.8.8.8
```

#### Endereço estático

```
# Exibe IP, máscara, gateway e DNS
netsh interface ipv4 show config

netsh interface ipv4 set address name="Wi-Fi" static 192.168.1.1 255.255.255.0 192.168.1.1

# Configuração de DNS manual  (1° Clouflare 2° Google)
netsh interface ipv4 set dnsservers name="Wi-Fi" static 1.1.1.1 primary

netsh interface ipv4 add dnsservers name="Wi-Fi" 8.8.8.8 index=2

# Testar resolução de nomes
ping google.com

nslookup google.com
```

Após ``static`` a ordem é: [Endereço IP do dispositivo] [Mascára da rede] [Gateway padrão]

OBS: Não usar endereços presentes no comando, modifique conforme os endereços da sua rede sendo ela IPv4 ou IPv6.

```
# Verificação de estado de interfaces
netsh interface show interface
```

#### Endereço DHCP (Automático)

```
netsh interface ipv4 show config name="Wi-Fi" source=DHCP

# Renovar endereço IP DHCP
ipconfig /release

ipconfig /renew
```

Outra forma

```
Tecla Windows + r

ncpa.cpl

Wi-Fi > Propriedades > TCP/IPv4 → Automático
```

#### Conexão de redes conhecidas pelo terminal 

```
Tecla Windows + r > CMD > Execute como administrador

netsh wlan shows networks

netsh wlan connect name="Nome_da_rede"
```

#### Problemas de DNS

```
# Libera cache de DNS
ipconfig /flushdns
```

#### Comandos úteis 

```
# Exibe tabela de roteamento IP
route print

# Exibe configurações de rede TCP/IP
ipconfig

# Consulta de dados do protocolo ARP
arp -a
```

