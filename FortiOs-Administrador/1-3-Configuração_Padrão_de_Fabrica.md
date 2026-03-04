# Configuração Padrão de Fábrica

O modo de Tradução de Endereço de Rede é o modo padrão de operação. Quais são as outras configurações padrão de fábrica? 

Conectar o cabo de rede do computador na porta 1 ou na porta interna do switch. Para modelos high-end e mid-range, conecte a interface de gerência. Em muitos modelos de entrada, existem o servidor DHCP na interface. Se o computador estiver com o DHCP habilitado, o computador irá receber um endereço IP. Para a acessar interface de gerência via web do FortiGate acesse: https://192.168.1.99. A informação de login padrão é de conhecimento público. Nunca deixe a senha em branco. Se a rede deve ser segura como a conta de admin do FortiGate. 






* IP: 192.168.1.99/24
  * Gerencia a interface em modelos em alto e média gama.
  * Port 1 ou interface interna em modelos de nível de entrada.
* Protocolos PING, HTTPS, e Protocolo SSH são gerencialmente habilitados.
* Servidor DHCP embutido é habilitado na porta 1 ou na interface interna.
  * Somente nos modelos de nível de entrada suportam o servidor dhcp.
* Login Padrão
  * Usuário: admin
  * Senha: (vazio)
    * Os dois são case sensitive.
* Pode-se acessar o FortiGate via CLI
  * Console sem rede
  * Widget de CLI Console e Emulador de Terminal, como o Putty ou Tera Term


