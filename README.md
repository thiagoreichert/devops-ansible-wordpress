Author: Thiago Reichert

Para este projeto é necessário Vagrant, Virtual Box instalados.

## Ansible



#### Comandos

ansible group -u user -i hosts -m interp -a command

ansible wordpress -u vagrant --private-key-file .vagra  -i hosts -m shell -a 'echo Hello World'



Verbose:

ansible -vvvv