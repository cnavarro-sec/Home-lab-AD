
LAB 1 – Acesso Inicial (Phishing Simulado)


Objetivo

Simular o comprometimento de credenciais através de um cenário de phishing e analisar os eventos gerados utilizando Wazuh e Sysmon.

Cenário
	
Um usuário do domínio acessou uma página corporativa falsa criada para fins de treinamento dentro do ambiente de laboratório.


Conta comprometida:  
  
Usuário: Megan

1. O usuário acessa uma página de login falsa.  
2. O comprometimento da credencial é simulado para fins educacionais.  
3. O atacante obtém uma credencial válida do domínio.  
4. A credencial é utilizada para iniciar a fase de reconhecimento e enumeração dos recursos da rede.


![](Pasted%20image%2020260524181919.png)


Técnicas MITRE ATT&CK  
  
- T1566 – Phishing  
- T1078 – Contas Válidas (Valid Accounts)

Resultados  
  
O atacante obteve acesso a uma conta válida do domínio, permitindo o início da fase de reconhecimento e enumeração do ambiente.  

Importante:

Nem sempre um invasor precisa explorar uma vulnerabilidade para entrar em um ambiente.
Credenciais válidas podem ser suficientes para iniciar um ataque.
O acesso inicial muitas vezes depende de engenharia social e erro humano.



Próximo Passo  


LAB 2 – Enumeração SMB e Descoberta de Compartilhamentos




