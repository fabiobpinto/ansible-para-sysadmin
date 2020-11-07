### Recomendação
Recomendo que não guardem senhas em arquivos como realizado nesse laboratório.

Essa prática que foi realizada aqui foi para não ficar tendo que digitar as senhas todas as vezes que acessa-se uma VM.

Você pode fazer os acessos de várias formas:
* Atravez de troca de chaves
* criptografando o arquivo de senha com o ansible-vault e na execução da Playbok usar o parametro --ask-vault-pass
* Usar os parametros com dados dos usuarios ao executar a playbook. Ex.: --user {usuario} -u {usuario} --ask-pass 
* Configurar o ansible.cfg para quando houver elevação de privilégios seja solicitada a senha de root. Como no exemplo abaixo:
```sh
 [privilege_escalation]
 become=True
 become_method=su
 become_user=root
 become_ask_pass=True
```
