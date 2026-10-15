# Vigia dos sites

Testa de fora, a cada 5 minutos, se os sites hospedados no VPS respondem.
Roda no GitHub Actions, então continua funcionando mesmo com o servidor fora
do ar — que é justamente quando o aviso importa.

- Lista de sites: `sites.txt` (um domínio por linha).
- Um site é considerado fora quando falha 3 vezes seguidas (sem resposta ou
  erro 5xx), com 10 segundos entre as tentativas.
- Quando algum site cai, a execução falha e o GitHub manda e-mail para a
  conta dona do repositório (aviso de "workflow falhou").
- O GitHub desliga agendamentos de repositórios parados há 60 dias; o
  `manter-ativo.yml` grava um registro por mês pra isso não acontecer.
