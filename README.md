# Instalação
    sudo su
    apt install isc-dhcp-server 
    
 # Configuração do isc-dhcp-server
    cd /etc/default/
    nano isc-dhcp-server
   ## Ubuntu 18: 
      INTERFACESv4="enp0s9" (Interface do Cliente)
      
   ## Ubuntu 14:
      INTERFACES="eth2" (Interface do Cliente)
      
 # Configuração do dhcpd.conf
    cd /etc/dhcp/
    nano dhcpd.conf
    
     ddns-update-style none;
     authoritative;
     log-facility local7;
     option domain-name-servers 192.168.10.10
     subnet 192.168.110.0 netmask 255.255.255.0 {
	      range 192.168.110.11 192.168.110.253;
	      option broadcast-address 192.168.110.255;
	      option routers 192.168.110.254;
	      option domain-name "lain.intranet";  
     }
# Reiniciando o DHCP
  ## Ubuntu 18: 
      systemctl restart isc-dhcp-server
  ## Ubuntu 14:
      service isc-dhcp-server restart
    
# Reserva de IP 
	host nomedodispositivo{
		hardware ethernet 00:00:00:00:00; (Exemplo de MAC Adress)
		fixed-address 192.168.100.123; (Exemplo de IP Fixo)
	}
	
![](https://github.com/w1redl4in/Servidor-DHCP/blob/master/2019-05-15-175032_1600x900_scrot.png)

 # Vídeo Prático
   [YouTube](https://youtu.be/9-2p9Ib4B6w)
