# LAB 2 – Enumeração SMB e Descoberta de Compartilhamentos

## Objetivo

Utilizar uma credencial válida obtida anteriormente para identificar compartilhamentos SMB disponíveis na rede.

## Cenário

Após obter acesso à conta Megan, foi realizada a enumeração de recursos SMB acessíveis dentro do domínio.

## Ataque

### Descoberta do host

![](img_lab_02/Pasted%20image%2020260525182151.png)

### Enumeração SMB

![](img_lab_02/Pasted%20image%2020260525182236.png)

### Listando arquivos da pasta

![](img_lab_02/Pasted%20image%2020260525191214.png)

### Vulnerabilidades nos arquivos

Possível ataque de de engenharia social
Identificação do funcionário interno

![](img_lab_02/Pasted%20image%2020260525191813.png)


![](img_lab_02/Pasted%20image%2020260525193716.png)


____

Descoberta de nomes de servidores internos.
Possibilidade de enumeração.
útil para movimentação lateral

![](img_lab_02/Pasted%20image%2020260525191942.png)

### Compartilhamentos encontrados

- Admin$
- C$
- FINANCE 
- IPC$

## Detecção

### Eventos observados no Windows

evento windows: 4624
evento ocorrido de logon com sucesso as 19:13

![](img_lab_02/Pasted%20image%2020260526001207.png)

evento windows:4634
logoff da conexao as 19:14


![](img_lab_02/Pasted%20image%2020260526001911.png)

evento:5140
acessou o C:\FINANCE


![](img_lab_02/Pasted%20image%2020260526004352.png)


Evento:5145

Usuário:  
CORP\MeganP  
  
Origem:  
192.168.210.7  
  
Compartilhamento:  
FINANCE  
  
Arquivo:  
servidores.txt  
onboarding.txt
fornecedores.txt
  
Tipo:  
File

![](img_lab_02/Pasted%20image%2020260526005528.png)
![](img_lab_02/Pasted%20image%2020260526005455.png)
![](img_lab_02/Pasted%20image%2020260526005424.png)


### Eventos observados no Wazuh

![](img_lab_02/Pasted%20image%2020260525210417.png)

---

Evento verificado:

19:13 ***Successful Remote Logon Detected - User:\MeganP - NTLM authentication, possible pass-the-hash attack - Possible RDP connection. Verify that PARROT is allowed to perform RDP connections

---

Ip de destino:
Agent.ip: 192.168.210.14

Ip de origem
ipAddress: 192.168.210.7

Usuario usado:
targetUserName: MeganP

OS do ip de origem
workstationName: PARROT

Indica login de compartilhamento de rede
logonType: 3

Autenticação:  
NTLMv2




![](img_lab_02/Pasted%20image%2020260525225650.png)

![](img_lab_02/Pasted%20image%2020260525225915.png)



Mitre&Attack

T1078 - Valid Accounts
T1021 – Remote Services
T1039 – Data from Network Shared Drive

## O que aprendi

- Compartilhamentos SMB podem revelar informações importantes sobre o ambiente.
- Contas comuns frequentemente possuem acesso de leitura a diversos recursos.
- A enumeração é uma das primeiras atividades realizadas após o acesso inicial.
- A telemetria do host pode auxiliar na identificação desse comportamento.

## Resultado

Foi realizada autenticação remota SMB utilizando credenciais válidas da conta CORP\MeganP. O acesso permitiu a enumeração e utilização do compartilhamento FINANCE. 
A atividade foi detectada pelo Wazuh através do evento Windows Security 4624 (Successful Logon) e da regra 92657 (Successful Remote Logon Detected). Após habilitação da auditoria detalhada de compartilhamentos, foi possível identificar o acesso ao arquivo `servidores.txt, onboarding.txt, fornecedores.txt por meio do evento 5145, permitindo correlacionar usuário, origem da conexão, compartilhamento e arquivo acessado.