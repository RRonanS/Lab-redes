## Instruções para executar um servidor TCP em Docker e solicitar um arquivo HTML


1. Inicie o Docker com o seguinte comando:

docker run -d -p 12000:12000 -it --rm --name <nome da empresa> -v "$PWD":/var/www/servidortctp -w /var/www/servidortctp python:2 python ./TCPServer.py

No meu caso o comando foi:
    docker run -d -p 12000:12000 -it --rm --name empresadesoftware -v "$PWD":/var/www/servidortctp -w /var/www/servidortctp python:2 python ./TCPServer.py
  
2. Copie o arquivo HTML que deseja disponibilizar para o Docker, utilizando o comando:

docker cp <nome do arquivo> <nome do container>:<caminho para qual ele será copiado>

Por exemplo:

docker cp index.html armarionet:/var/www/servidortctp/

3. Verifique se o arquivo HTML foi carregado corretamente no Docker, executando o comando:

docker exec armarionet ls /var/www/servidortctp/

4. Para acessar o arquivo HTML, utilize o comando:

wget localhost:<porta configurada>

Substitua `<porta configurada>` pela porta configurada no comando de inicialização do Docker. Neste exemplo, a porta configurada é 12000, portanto o comando seria:

wget localhost:12000

O arquivo HTML será baixado e salvo na pasta atual do terminal.
