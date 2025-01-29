Nesse lab vamos criar um "device number" e "linux device file"


~~~~~~~~~~~~
** Device Number (Número do Dispositivo)

Todo dispositivo no Linux é representado por um número único chamado Device Number, que tem dois componentes:

    Major Number (Número principal): Identifica o tipo de dispositivo e qual driver será usado para acessá-lo.
    Minor Number (Número secundário): Diferencia múltiplos dispositivos do mesmo tipo.

Os números de dispositivo são registrados no kernel ao criar um driver.

 $ cat /proc/devices

~~~~~~~~~~~~

~~~~~~~~~~~~
Device File (Arquivo de Dispositivo)

No Linux, os dispositivos de hardware são acessados como arquivos especiais chamados Device Files dentro do diretório /dev/. Esses arquivos permitem que programas interajam com dispositivos de forma semelhante à leitura e escrita em arquivos comuns.

    Tipos de arquivos de dispositivos:
        Dispositivos de caractere (c): Transmitem dados como um fluxo de bytes (exemplo: terminais, portas seriais).
        Dispositivos de bloco (b): Manipulam dados em blocos (exemplo: discos rígidos).
        Dispositivos de rede (não aparecem em /dev/ diretamente, são gerenciados pelo kernel).

~~~~~~~~~~~~


para mostrar esse drivers numeros voce pode usar :
$ ls -al /dev/tty*
a quinta , numero maior, e sexta, numero menor, colunas desta lista mostram esse numeros que conectam drivers a dispositivos.

antes de comecar as mudancas, eh bom olhar a atual lista de nuremos de devices com seus respectivos modulos:
    
    $ cat /proc/devices

1 - para construir o objeto dev_nr.ko:
    
    $ make 

2 - para carregar o modulo criado "my_dev_nr" e que esta ligado ao numero "64(numero maior) e 0 (numero menor)"
    
    $ sudo insmod dev_nr.ko

3 - para ver esse numero dentro do sistema:
    
    $ cat /proc/devices | grep my_dev_nr


4 - para conectar/atribuir um "device file/arquivo de dispositivo"=mydevice ao numero de device criado 90,0 -> isso cria um device linkado a 90,0, (c para dispositivo de caractere)
    
    $ sudo mknod /dev/mydevice c 64 0

5 - para ver esse dispositivo criada:
    
    $ ls /dev/mydevice -al

6 - para criar p programa de teste de comunicacao com esse novo dispositivo criado:

    $ gcc test.c -o test; sudo chmod 666 /dev/mydevice; ./test; sudo dmesg | tail -n 5

No final o autor sugere:

sudo mknod /dev/mydevice c 64 0
Para criar um device file.
