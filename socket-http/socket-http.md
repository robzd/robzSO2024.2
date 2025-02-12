# Tutorial: Criando um Servidor HTTP Simples em Python

## Informações gerais
- **Público alvo**: alunos da disciplina de SO (Sistemas Operacionais) do curso de TADS (Superior em Tecnologia em Análise e Desenvolvimento de Sistemas) no CNAT-IFRN (Instituto Federal de Educação, Ciência e Tecnologia do Rio Grande do Norte - Campus Natal-Central).
- disciplina: **SO** Sistemas Operacionais
- professor: [Leonardo A. Minora](https://github.com/leonardo-minora)
- aluno: Robson Douglas Fernandes de Araújo
- texto gerado pelo [Microsoft Copilot](https://copilot.microsoft.com/)


### Experimento
1. Servidor HTTP **sem thread**:
2. Execução de clientes
   1. apenas 1 cliente: funcionamento normal
   2. 2 clientes simultâneos: funcionamento normal
   3. 5 clientes simultâneos: a requisição get do client retorna algumas informações de forma dessincronizada
   4. 10 cliente simultâneos: a requisição get do client retorna as informações ainda mais dessincronizadas, por vezes misturando o "status", "motivo" e "conteúdo" de uma requisição com outra


1. Servidor HTTP **com thread**:
2. Execução de clientes
   1. apenas 1 cliente: funcionamento normal
   2. 2 clientes simultâneos: funcionamento normal
   3. 5 clientes simultâneos: a requisição get do client retorna as informações bastante dessincronizadas, ainda mais do que o servidor sem threads usando 10 clientes simultaneos
   4. 10 cliente simultâneos: a requisição get do client retorna as informações mais dessincronizadas ainda, juntando "status", "motivo" e "conteúdo" de várias requisições juntas

### Diferença entre os servidores **sem** e **com** threads
Em ambos os casos, todas as informações foram retornadas, porém a partir de 5 clientes simultâneos, o funcionamento do get response começa a ter respostas "embaralhadas", principalmente quando o servidor está utilizando threads. Apesar disso, os conteúdos html retornados
ficaram separados uns dos outros, acredito que por se tratarem de um conteúdo mais pesado do que um simples status numérico ou conteúdo vazio.
