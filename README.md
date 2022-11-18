# ftp-action-studies

Automatize o envio de arquivos de FTP do seu site para o seu site lw!

## Exemplo de uso

```
name: Deploy via ftp
on: push
jobs:
  deploy:
    name: Deploy
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2

    - name: studies-lwftp-testing
      uses: allanalves23/ftp-action-studies@0.0.4
      with:
        host: ${{ secrets.HOST }} 
        user: ${{ secrets.USER }}
        password: ${{ secrets.PASS }}
        localDir: "dist"
```

## Parâmetros de uso

Parâmetro | Descrição | É requerido? | Padrão
--- | --- | --- | ---
host | Servidor FTP | Sim | N/A
user | Usuário FTP | Sim | N/A
password | Senha do usuário FTP | Sim | N/A
localDir | Diretório do projeto a ser copiado a sua hospedagem | Não | .
remoteDir | Diretório da sua hospedagem que irá receber os arquivos copiados | Não | 'public_html'
forceSsl | Forçar encryptação SSL | Não | false
options | Opções adicionais ao uso do comando [lftp](http://lftp.yar.ru/lftp-man.pdf) | Não | ''
