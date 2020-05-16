Author: Thiago Reichert

Para este projeto é necessário Vagrant, Virtual Box instalados.

## Ansible

Instalação de wordpress apenas via Ansible com PHP 5.6, MySQL, e Apache.



#### Comandos

Com a chave e hosts configurados:

ansible-playbook provision.yml -i hosts

Exemplo genérico:

ansible group -u user -i hosts -m interp -a command

Comando completo por baixo dos panos.

ansible wordpress -u vagrant --private-key-file .vagra  -i hosts -m shell -a 'echo Hello World'



Verbose:

ansible -vvvv