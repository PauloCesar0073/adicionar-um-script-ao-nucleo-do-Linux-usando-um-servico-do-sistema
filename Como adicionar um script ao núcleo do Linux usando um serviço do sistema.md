## Como adicionar um script ao núcleo do Linux usando um serviço do sistema

1. Crie um novo arquivo para o serviço do sistema no diretório `/etc/systemd/system/`. Você pode usar qualquer nome, desde que termine com a extensão `.service`. Por exemplo, vamos usar `meuscript.service`:

   ```
   sudo nano /etc/systemd/system/meuscript.service
   ```

2. No arquivo `meuscript.service`, adicione o seguinte conteúdo:

   ```
   [Unit]
   Description=Meu script do sistema
   
   [Service]
   ExecStart=/caminho/para/o/seu/script.sh
   
   [Install]
   WantedBy=multi-user.target
   ```

   Substitua `/caminho/para/o/seu/script.sh` pelo caminho completo para o seu script.

3. Salve e feche o arquivo.

4. Recarregue os arquivos de configuração do systemd:

   ```
   sudo systemctl daemon-reload
   ```

5. Inicie o serviço:

   ```
   sudo systemctl start meuscript
   ```

Agora o seu script será executado como parte do sistema operacional. Você também pode habilitar o serviço para que ele seja iniciado automaticamente durante a inicialização do sistema:

```
sudo systemctl enable meuscript
```

Dessa forma, o script será executado sempre que o sistema for iniciado.
