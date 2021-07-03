# Múltiplas chaves SSH para contas diferentes no Github ou Gitlab

## Passos:
  - Criar a chave RSA para utilizar o gitlab:
    - Executar o comando `ssh-keygen -t rsa -b 2048 -C "<email-gitlab>"`
    - Irá exebir os campos para a criação das chaves pública e privada: "Generating public/private rsa key pair. Enter file in which to save the key ->(/home/user_name/.ssh/id_rsa_gitlab): "Informar o path e o nome da chave => `(/home/user_name/.ssh/id_rsa_gitlab)`" 
    - Copiar a chave pública e adicionar ela no GitLab;
 
 - Criar a chave RSA para utilizar o github:  
    - Executar o comando `ssh-keygen -t rsa -b 2048 -C "<email-github>"`
    - Irá exebir os campos para a criação das chaves pública e privada: "Generating public/private rsa key pair. Enter file in which to save the key ->(/home/user_name/.ssh/id_rsa): "Informar o path e o nome da chave => `(/home/user_name/.ssh/id_rsa_github)`" 
    - Copiar a chave pública e adicionar ela no GitHub;

 - Criar o arquivo config em **_~/.ssh_**, e criar a seguinte configuração:
   ```shell
   # Gitlab Account
     Host gitlab.company_url.com
       HostName gitlab.company_url.com
       PreferredAuthentications publickey
       IdentityFile ~/.ssh/id_rsa_gitlab

   # GitHub Account
     Host github.com
       HostName github.com
       PreferredAuthentications publickey
       IdentityFile ~/.ssh/id_rsa_github
   ```
   
   ### Arquivo modelo disponível => [config](https://github.com/harisson-freitas/config-ssh/blob/main/config)
