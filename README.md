# upgrade-packages
Roles de Ansible para actualizar paquetes con la posibilidad de excluir aquellos que no se desee que se actualicen.

Por defecto no se excluirá ningún paquete de la actualización, para excluir paquetes agrégelos como parámetros a la
hora de ejecutar el playbook como se muestra en los siguientes ejemplos:

	· Para RedHat: -e '{"rh_pkgs": [python3,nginx]}'
	· Para Debian: -e '{"deb_pkgs": [python3,nginx]}'

Por defecto no se reiniciará el sistema tras la actualización de paquetes, para ello especifique si desea que se reinicie
el sistema como parámetro a la hora de ejecutar el playbppk como en el siguiente ejemplo:

	· -e reboot=[Y,y,yes]

Por ejemplo, si deseamos actualizar todos los paquetes menos python3 y nginx y que además se reinicie el sistema tras la
actualización, deberemos ejecutar el playbook de la siguiente manera:

	· ansible-playbook -i hosts -e '{"rh_pkgs": [python3,nginx]}' -e '{"deb_pkgs": [python3,nginx]}' -e reboot=y start.yml
