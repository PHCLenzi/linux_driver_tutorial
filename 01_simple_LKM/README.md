Aqui vamos criar um primeiro modulo sem estar relacionado com um dispositivo ainda.


1 - $make

2 - $sudo insmod mymodule.ko

3 - Para mostrar os modulos ativos:
    $lsmod 

4 - Para ver saida de texto no log do kernel:
    $sudo dmesg

5 - Para remover o modulo do kernel:
    $sudo rmmod mymodule

6 - Para ver mensagem de desligamento no log do kernel:
    $sudo dmesg

7 - Para limpar todo o diretorio executar:
    $make clean