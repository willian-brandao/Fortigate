# Ciclo de Vida do Pacote
<img width="1208" height="691" alt="image" src="https://github.com/user-attachments/assets/8c5d3999-6a83-45f5-9dc7-d2b8cd06e696" />

Todo o pacote que passa pelo Fortigate passa por determinados processos, alguns obrigatórios e outros opcionais. Quando o pacote chega pela interface de rede, ele passa pelos controles obrigatórios de ACL, detectand se existe essas informações em uma blacklist, depois pelo HPE (mecanismo de proteção de host), onde se é verificado se trata de Dos, após esse passo passa pelo IP Integrity header check,onde se é validado se o cabeçalho foi modificado, e caso tenha vindo de uma VPN, o pacote é desencapsulado.

## Dentro do kernel, o pacote passa por mais outras etapas:

* Obrigatórias
  *  DNAT - Caso o endereço de destino precisar ser traduzido.
  *  Routing, RPF check, SD-WAN - decide por qual porta o pacote deve sair e verifica se o caminho de volta é valido. 
  *  Stateful Inspection / policy lookup / session management - cria uma ficha da conexão e verifica qual política de firewall se aplica. 
  *  Session helpers - auxilia protocolos como FTP ou SIP que abrem porta dinâmicas. 

* Opcionais
  * User authentication - Se a política exigir login do usuário.
  * Device identification - Identifica se o dispositivo é um celular, PC, etc.
  * SSL VPN - Se o tráfego for para o portal VPN.
  * Local management traffic - Tráfego destinado ao próprio FortiGate (SSH, HTTPs admin)

## UTM / NGFW (Inspeção de segurança)

  Flow-based inspection - O pacote é inspecionado em fluxo ( mais rápido, menos memória, menos consumo de recurso)

  Proxy-based inspection - O Fortigate age como proxy, reconstruindo o conteúdo (mais seguro, porém usa mais recurso)

  Explicity web proxy - caso tenha configurado o proxy explícito

  Bonet check - verifica se o destino é um servidor de botnet 

  Flow-based pode usar NP/CP combinados.

## Kernel - segunda passagem (Forwarding e  SNAT)

* Forwarding - Encaminha o pacote para a interface de saída (obrigatório).
* Source NAT (SNAT) - Se necessário, troca o IP de origem (para sair à internet)
* Offloadável para NP

## Saída: criptografia VPN e modelagem de tráfego 
* IPsec VPN encryption - Se o pacote deve ser encryptado para uma VPN - opcional.
* Traffic shaping - Aplica limites de banda ou priorização
* IPsec pode usar NP para criptografia acelerada.

## Analogia final (modo história)

O entregador (pacote) chega no prédio do FortiGate.

Primeiro portão: verificam se ele está na lista negra (ACL) e se o uniforme está íntegro (IP integrity).

Catraca do Kernel: trocam o nome do destinatário se necessário (DNAT), consultam o mapa (roteamento) e abrem uma ficha (session).

Se você contratou segurança extra (UTM): ele passa pelo escâner de bagagem (flow/proxy) e por um detector de máfia (botnet).

Saída: trocam o nome do remetente (SNAT) e, se for para uma área segura, colocam uma capa criptografada (IPsec).

Último portão: ele sai.

Tudo que pode ser feito por esteiras automáticas (NP/CP) é acelerado. O que é personalizado (usuário, dispositivo, proxy) vai no braço (CPU).
  

  





