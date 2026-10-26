# FICHA DE DECISÕES · War Room FiapBank (CP6 · 3 aulas)

> Este arquivo é o **README.md do repositório do grupo** (`cp6-warroom-<nome-do-grupo>`).
> Vale **5,0 pontos** (rodadas 0,5 · relâmpagos 0,3), e a nota é pela
> **justificativa**, não pela letra. Preencham após cada aula e commitem até
> **23h59 do mesmo dia** (regras completas na seção 5 do enunciado).
>
> **Os incidentes da madrugada são revelados só em aula.** O título de cada registro
> será **ditado pelo professor na hora**; ninguém se antecipe.

**Grupo (nome da equipe plantonista):** GrupoFlashFix

**Turma:** 2CCPG **Repo:** `cp6-warroom-GrupoFlashFix`

**Integrantes (nome + RM):**

| Nome                               | RM         |
| ---------------------------------- | ---------- |
| Bruno Anselmo da Silva             | RM: 566521 |
| Fernando de Almeida Godoi Martines | RM: 564820 |
| Gabriel Ber Soares Tarone          | RM: 563520 |
| Guilherme de Freitas Salgado       | RM: 562494 |
| Vinicius Ribeiro Dias              | RM: 566468 |

## 0. Setup do repositório (antes da 1ª aula; podem apagar esta seção depois)

1. Um integrante cria o repo **público** no GitHub: `cp6-warroom-<nome-do-grupo>`
   (ex.: `cp6-warroom-debugadores`), com um README qualquer
2. Substituam o conteúdo do `README.md` por este template (no navegador, pelo próprio
   GitHub, ou clonando):
   ```bash
   git clone https://github.com/<conta>/cp6-warroom-<nome-do-grupo>.git
   cd cp6-warroom-<nome-do-grupo>
   # substitua o conteúdo do README.md por este template e:
   git add .
   git commit -m "chore: ficha em branco do grupo"
   git push
   ```
3. Postem o **link no Teams** (o mesmo link para todo o grupo)

**Convenção de commits** (1 commit por rodada; relâmpagos podem ir junto com a
rodada seguinte):

```
decisao: R1 - opcao C (<resumo da justificativa em uma frase>)
decisao: R2 - opcao A (<resumo em uma frase>)
pos-mortem: relatorio de incidente da madrugada
```

---

## 📁 Dossiê técnico do FiapBank (MVP em produção)

**Stack:** Java 17 + Spring Boot + Spring Data JPA + Oracle. API com endpoints em
`/api/contas` e `/api/transferencias` (cenário visto desde a Aula 13).

**Contrato e regras de negócio que o banco prometeu aos clientes e aos reguladores:**

| Regra                    | Como deve ser                                                                    |
| ------------------------ | -------------------------------------------------------------------------------- |
| Transferência **PIX**    | taxa **R$ 0,00**                                                                 |
| Transferência **TED**    | taxa fixa **R$ 5,00**                                                            |
| Saldo                    | **nunca fica negativo**: transferência/saque sem saldo é recusado com erro claro |
| Número de conta          | **sequencial e único** (1001, 1002, 1003...), gerado pelo sistema                |
| Extrato de transferência | grava **quem pagou** e **quem recebeu**, na ordem certa                          |
| CPF                      | **dado sensível**: nunca aparece nas respostas da API                            |
| Consultas ao banco       | sempre parametrizadas, e cada operação **usa e libera** a conexão                |
| Suíte de testes          | roda antes de todo deploy; **verde** é pré-requisito pra subir                   |

**Como escrever a justificativa:** nomeie o **mecanismo técnico** em jogo (o
conceito das Aulas 11 a 15 que explica o incidente) e o **trade-off** (velocidade ×
segurança × faturamento × dívida). "Porque é mais seguro" não é justificativa.

---

# 📝 REGISTRO DE DECISÕES

> A cada incidente, o professor dita o título (ex.: "Rodada 1"). **Copiem o modelo
> abaixo, colem no fim desta seção** e preencham com o rascunho feito em aula, junto
> com o **placar do grupo** após a consequência. Commitem 1 commit por rodada até
> 23h59 do dia.
>
> **Eventos relâmpago:** registrem apenas se o grupo for **afetado** (o professor
> chama quem for; não ser chamado é bom sinal).

**Decisões do gupo na Aula 1:**

## Dia 1 - qui 19h → 23h

_(as decisões entram aqui, na ordem em que a madrugada as trouxer; placar inicial:
🔥 ** · 💰 ** · 🧹 \_\_)_

Problema Inicial:

**Rodada 1**

Voto D
Realizar um Rollback para a versão de Terça-Feira
🔥 -1 · 💰 R$ 15 mil · 🧹 +1

Justificativa:
Seria a versão mais segura para seguir, visto que tomar uma decisão de "hotfix" agora sem teste apresenta maior risco para futuros bugs, existe a possibilidade de o rollback ter arrumado bugs anteriores e tais bugs virão aparecer no futuro, necessário fix rápido.

---

**Relâmpago A**

Opção escolhida:
B) Usar a query delivery

🧹 -1 🔥 +1 para todos que escolheram B

**Rodada 2**:

Opção escolhida:
A) PreparedStatement parametrizado agora

🔥0 | 💰 0 | 🧹 0

**Relâmpago B**

Questão Relâmpago:: Opção escolhida: A)

🔥0 | 💰 0 | 🧹 0

**Rodada 3**

Opção escolida:
A) Corrigir o getInstancia do singleton para guardar a instância

🔥 +1 | 💰 5 mil

## Pontuação Final (DIA 1): 🔥 +1 | 💰 R$ 20 mil | 🧹 0

## Dia 2 - qui 00h → 04h

**Rodada 4**

Decisão: B) Corrigir o código e reprocessar os extratos antigos.
Justificativa: corrigir apenas o código não resolve os registros incorretos já existentes. O reprocessamento corrige o histórico das transferências, mantendo a confiabilidade dos comprovantes sem movimentar o dinheiro novamente.

🔥 +1 | 💰 R$ 25 mil | 🧹 -1


**Rodada 5**

Decisão: A) Aplicar fail-fast na factory.
Justificativa: retornar null faz o erro aparecer longe de sua origem e dificulta o diagnóstico. Uma exceção clara identifica imediatamente o tipo não suportado. Como a conta Universitária é válida, também será necessário implementar sua criação na factory para liberar os cadastros.

🔥 -1 | 💰 R$ 0 | 🧹 0

**⚡ EVENTO RELÂMPAGO**

Decisão: B) Utilizar Builder com valores padrão.
Justificativa: o Builder facilita a criação flexível de objetos sem exigir diversos construtores. Valores padrão podem ser usados para campos opcionais, mas dados obrigatórios, como CPF e tipo de conta, devem ser validados antes de efetivar o cadastro.

🔥 0 | 💰 R$ 0 | 🧹 0

**Rodada 6**

Decisão: B) Investigar o problema, mesmo que seja necessário perder a janela de deploy.
Justificativa: o código cobra R$ 50,00, mas o contrato estabelece uma taxa TED de R$ 5,00. Alterar ou desabilitar o teste esconderia uma possível falha financeira. A prioridade é corrigir a implementação e validar os testes antes de publicar a versão, evitando cobranças incorretas aos clientes.

🔥 -1 | 💰 R$ 30 mil | 🧹 -1

## Pontuação Final (DIA 2): 🔥 0 | 💰 R$ 75 mil | 🧹 0


## 🔎 O caminho do MEU grupo (preencher na 3ª aula, quando o mapa for revelado)

Uma linha por decisão registrada acima (usem os títulos ditados em aula):

**Pontuação Inicial: | 🔥 7 · 💰 R$ 0 · 🧹 2 |**

| #   | Decisão | Nossa letra | Consequência que ELA teria tido |
| --- | ------- | ----------- | ------------------------------- |
|  1  | Realizar um Rollback para a versão de Terça-Feira |  D)     | 🔥 -1 · 💰 R$ 15 mil · 🧹 +1 |
|  R. Relâmpago A |  Usar a query delivery |    B)       | 🔥 · 💰 · 🧹-1 |
|  2  |   PreparedStatement parametrizado agora     |      A)     | 🔥 · 💰  · 🧹   |
|  R. Relâmpago B |         |     A)      | 🔥 · 💰  · 🧹  |
|  3  | Corrigir o getInstancia do singleton para guardar a instância |     A)      |  🔥 +1 · 💰 5 mil · 🧹 |
|  4  | Corrigir o código e reprocessar os extratos antigos. |      B)     | 🔥 +1 · 💰 R$ 25 mil · 🧹 -1 |
|  5  | Aplicar fail-fast na factory. |     A)      | 🔥 -1 · 💰  · 🧹   |
|  R. Relâmpago C | Utilizar Builder com valores padrão. |   B)    | 🔥  · 💰  · 🧹  |
|  6  | Investigar o problema, mesmo que seja necessário perder a janela de deploy. |    B)       | 🔥 -1 · 💰 R$ 30 mil · 🧹 -1 |
## Pontuação Final : 🔥 6 | 💰 R$ 75 mil | 🧹 0


---

# 📋 PÓS-MORTEM · relatório de incidente (montar em sala na 3ª aula)

> Rascunho em aula e commit final `pos-mortem:` até 23h59 do dia da 3ª aula.

# Relatório WarRoom — FIAP Bank

## 1. Linha do tempo da madrugada

- **19h — Início da crise:&#x20;**&#x64;iante de um problema no sistema na véspera da Black Friday, a equipe optou por realizar um rollback para uma versão anterior. A partir daí, foi necessário lidar com problemas técnicos e consequências das decisões tomadas durante a madrugada.
- **19h12 —  Rodada 1: identificamos uma vulnerabilidade de SQL Injection em uma consulta JDBC e optamos por corrigi-la utilizando&#x20;**`PreparedStatement` parametrizado.
- **Consequência da Rodada 1 —&#x20;**&#x20;descobrimos um vazamento de conexões com o banco de dados, que poderia esgotar o pool. A decisão foi utilizar `try-with-resources` para fechar os recursos automaticamente.
- **22h50 — Rodada 3:** contas diferentes receberam o mesmo número, `1001`, devido a um erro na implementação do Singleton. Escolhemos corrigir o método para reutilizar a mesma instância.
- **00h47 — Rodada 4:** um comprovante PIX registrava incorretamente a origem e o destino da transferência, apesar de os saldos estarem corretos. Decidimos corrigir a gravação e reprocessar os extratos antigos, sem movimentar o dinheiro novamente.
- **01h30 — Rodada 5:** os cadastros da Conta Universitária falhavam porque a fábrica retornava `null` para tipos não reconhecidos. Escolhemos implementar o tratamento fail-fast, com uma exceção clara para tipos não suportados.
- **02h20 — Evento Relâmpago C:** o marketing solicitou cadastros contendo apenas nome e saldo. Escolhemos utilizar o padrão Builder com valores padrão para facilitar a construção dos objetos, mantendo a validação dos campos obrigatórios.
- **03h45 — Rodada 6:** um teste revelou que a taxa TED estava sendo calculada como R$ 50,00, embora o contrato previsse R$ 5,00. Decidimos investigar e corrigir o problema, mesmo com o risco de perder a janela de deploy.
- **04h00 — fechamento da janela de deploy:** horário-limite para publicação das alterações antes do congelamento previsto para a Black Friday.
- **08h00 — abertura prevista da campanha:** horário estabelecido pelo diretor para o início da campanha, aumentando a pressão sobre a equipe para resolver os problemas sem comprometer a segurança e a confiabilidade do sistema.

## 2. Causa raiz de 2 incidentes (aula + mecanismo técnico)

**Incidente 1: Vulnerabilidade de SQL Injection na busca de contas**

**Aula/mecanismo:** segurança em banco de dados e consultas parametrizadas com JDBC.

A causa raiz era a construção de uma consulta SQL por concatenação direta do nome informado pelo usuário. Isso permitia que uma entrada fosse interpretada como parte do comando SQL. A solução escolhida foi utilizar `PreparedStatement`, separando os dados da instrução SQL e reduzindo o risco de SQL Injection.

**Incidente 2: Duplicidade de números de conta**

**Aula/mecanismo:** padrão de projeto Singleton e gerenciamento do estado de objetos.

A causa raiz estava no método `getInstancia()`, que criava um novo objeto `GeradorNumeroConta` a cada chamada, reiniciando o contador em `1001`. Escolhemos corrigir o método para reutilizar a instância, evitando que o contador fosse reiniciado a cada chamada no cenário apresentado.

## 3. O que faríamos diferente (2 rodadas + por quê)

**Rodada 5 — Conta Universitária**

Reconsideraríamos a decisão e retiraríamos temporariamente a Conta Universitária da campanha até que sua implementação estivesse pronta e testada. A abordagem fail-fast melhora o diagnóstico, mas, sozinha, não implementa o suporte ao novo tipo de conta. Seria mais seguro liberar o produto somente depois de garantir que a fábrica reconhece o tipo `UNIVERSITARIA` e consegue criar a conta corretamente.

**Rodada 6 — Teste da taxa TED**

Manteríamos a decisão de investigar o erro, mas executaríamos os testes automatizados continuamente durante o desenvolvimento e antes da janela de deploy. Assim, a divergência entre R$ 5,00 e R$ 50,00 poderia ser descoberta mais cedo, reduzindo a pressão da madrugada e o risco de atrasar a publicação. Não desabilitaríamos o teste nem alteraríamos o valor esperado apenas para liberar o deploy.

## 4. A maior lição da equipe

A maior lição foi que a pressão por cumprir prazos não pode ser maior que a responsabilidade de manter um sistema financeiro confiável. Em uma crise, é necessário identificar a causa raiz dos problemas, corrigir as falhas e validar as soluções antes de publicar alterações. Esconder erros ou priorizar apenas a velocidade pode transformar um problema técnico em prejuízo financeiro e perda de confiança dos clientes. A comunicação e a colaboração da equipe são essenciais para tomar decisões responsáveis, mesmo quando isso significa adiar uma entrega.
