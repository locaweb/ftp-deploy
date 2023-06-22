# ftp-deploy

Automatize o envio de arquivos de FTP do seu site para o seu site Locaweb!

## Exemplo de uso

```
name: Deploy via ftp
on: push
jobs:
  deploy:
    name: Deploy
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3

    - name: FTP Deploy Locaweb
      uses: locaweb/ftp-deploy@1.0.0
      with:
        host: ${{ secrets.HOST }} 
        user: ${{ secrets.USER }}
        password: ${{ secrets.PASS }}
        localDir: "dist"
```


> Disclaimer: Use secrets para os dados de acesso do seu Servidor FTP, segredos evitam de você expor dados sensíveis no seu código fonte. Para mais detalhes de uso de secrets no github acesse https://docs.github.com/en/actions/security-guides/encrypted-secrets 

## Parâmetros de uso

Parâmetro | Descrição | É requerido? | Padrão
--- | --- | --- | ---
host | Host | Sim | N/A
user | Usuário de FTP | Sim | N/A
password | Senha | Sim | N/A
localDir | Diretório do projeto a ser copiado a sua hospedagem | Não | .
remoteDir | Diretório da sua hospedagem que irá receber os arquivos copiados, **caso sua hospedagem for Windows use o valor 'web'** | Não | 'public_html'
forceSsl | Forçar encryptação SSL | Não | false
options | Opções adicionais ao uso do comando [lftp](http://lftp.yar.ru/lftp-man.pdf) | Não | ''
