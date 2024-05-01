
# Como configurar um servidor de CS2? - O Guia

- **Pre-requisitos do servidor**:
  RAM: 2GB
  Armazenamento: 33GB
  CPU: minim x86-64-v2
 
 - GUIA BASEADO EM: https://hub.tcno.co/games/cs2/dedicated_server/

Antes de tudo, você deverá ir até o: https://steamcommunity.com/dev/managegameservers e registrar o ID do servidor. 

1. Instalar a Steam e CS2.
2. Navegar até `C:\Program Files (x86)\Steam\steamapps\common\Counter-Strike Global Offensive\game\bin\win64`
3. Abrir o Sublime (ou qualquer outro editor de texto) e criar um arquivo chamado `server.bat`
4.  Nesse arquivo, inserir o seguinte conteúdo: 

    `cd "<CS2_PATH>"` <br>
   `start /wait cs2.exe -dedicated -usercon -console -secure -dev +game_type 0 +game_mode 1 +sv_logfile 1 -serverlogging +sv_setsteamaccount <SERVER_ID> +map de_inferno +exec server.cfg`<br>

Substituindo o `CS2_PATH` pelo caminho do arquivo cs2.exe e o `SERVER_ID` pelo ID do servidor previamente registrado. 

5. Navegar até: `C:\Program Files (x86)\Steam\steamapps\common\Counter-Strike Global Offensive\game\csgo\cfg` e inserir os aquivos `server.cfg` `comp.cfg` e `live.vcfg` presentes no diretório **`cfg`**.
6. Abrindo a porta do servidor para outros computadores em LAN poderem se conectar ao servidor.

 - Execute o seguinte comando como admnistrador no powershell: 
 

`New-NetFirewallRule -DisplayName "CS2 Server" -Direction Inbound -LocalPort 27015,27016 -Protocol TCP -Action Allow` <br>
`New-NetFirewallRule -DisplayName "CS2 Server" -Direction Inbound -LocalPort 27015,27016 -Protocol UDP -Action Allow` <br>
`New-NetFirewallRule -DisplayName "CS2 Server" -Direction Outbound -LocalPort 27015,27016 -Protocol TCP -Action Allow` <br>
`New-NetFirewallRule -DisplayName "CS2 Server" -Direction Outbound -LocalPort 27015,27016 -Protocol UDP -Action Allow` <br>

- Caso esteja usando algum anti-virus ou firewall e o passo acima deu errado, você tem que permitir o acesso ao servidor (vide https://www.windowscentral.com/how-open-port-windows-firewall) 
