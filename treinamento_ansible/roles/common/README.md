Role Common
=========

Role common a todos os servidores, será copiado o banner e backup para os servidores.


Role Variables
--------------

No arquivo motd é utilizado duas variáveis para sua criação, essas variáveis são o FQDN e o IPV4.

Dependencias
------------

Necessita do arquivo de Backup.tar.gz e modt para ser copiado para os Servidores de Destino

Example Playbook
----------------

Abaixo tem o modelo de declaração da Playbook.yml

    - hosts: servers
      roles:
         - common

License
-------

BSD

Author Information
------------------

Fábio Brito Pinto - fabiobritopinto@gmail.com
https://www.linkedin.com/in/fabiobritopinto/
