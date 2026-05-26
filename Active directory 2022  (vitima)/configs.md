
corp.local



configurando server ad habilitando DNS server e AD Domain service

![](Pasted%20image%2020260509125736.png)

ao entrar no server maneger na menssagem em amarelo ele pede parar configurar o domain controller, configurando o domain controller adicionando a floresta corp.local no ad e senha Gatita13060

![](Pasted%20image%2020260509130733.png)

apos a configuracao reiniciado

configurando usuarios e grupos em tools

![](Pasted%20image%2020260509135529.png)

criando usuarios na unidade organizacional

![](Pasted%20image%2020260509141631.png)


ORGANOGRAMA

![](Pasted%20image%2020260509145919.png)

criado os grupos no ad de departamentos e grupos e usuarios

![](Pasted%20image%2020260509155620.png)

adicionando usuarios aos grupos conrrespondentes no AD
![](Pasted%20image%2020260512071835.png)

Possibilidades:
técnico promovido errado
permissão excessiva

1: VUL
adicionando algumas vulnerabilidades User victor com Domain Admins no MemberOf
![](Pasted%20image%2020260512073135.png)




vul2:

Criando servicos  sql backup e deploy

![](Pasted%20image%2020260512100926.png)


possibilidades
Kerberoasting
password spraying



Vul3: setspn -A HTTP/web.corp.local sqlsvc
habilita kerberoasting

![](Pasted%20image%2020260515191404.png)



podendo ser usado no parrot:
GetUserSPNs.py corp.local/user:senha -dc-ip IP

e quebra de senhas

hashcat -m 13100 hash.txt wordlist.txt