Author: Thiago Reichert

Para este projeto é necessário Vagrant, Virtual Box instalados.

## Ansible

Instalação de wordpress automatizado subindo VMs CentOS com Vagrant, e Ansible para provisionar PHP 5.6, MySQL, e Apache.

Projeto Ansible possui tasks, roles, templates, dependencies, handlers.



### Como utilizar

1 - Baixar o projeto

2 - No diretório executando o comando vagrant up para subir as VMs.

3 - Acessar a máquina ansible utilizando o comando "vagrant ssh ansible"

4 - Na máquina acessar o diretório que possui os arquivos do ansible: "cd /vagrant"

5 - Executar o comando "ansible-playbook provision.yml -i hosts"



#### Comandos

Com a chave e hosts configurados:

ansible-playbook provision.yml -i hosts

Exemplo genérico:

ansible group -u user -i hosts -m interp -a command

Comando completo por baixo dos panos.

ansible wordpress -u vagrant --private-key-file .vagra  -i hosts -m shell -a 'echo Hello World'



Verbose:

ansible -vvvv