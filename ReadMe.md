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
Voto D
Realizar um Rollback para a versão de Terça-Feira
🔥 -1 · 💰 R$ 15 mil · 🧹 +1

Justificativa:
Seria a versão mais segura para seguir, visto que tomar uma decisão de "hotfix" agora sem teste apresenta maior risco para futuros bugs, existe a possibilidade de o rollback ter arrumado bugs anteriores e tais bugs virão aparecer no futuro, necessário fix rápido.

---

**Rodada 1**

Opção escolhida:
B) Usar a query delivery

🧹 -1 🔥 +1 para todos que escolheram B

Questão Relâmpago:

Opção escolhida:
A) PreparedStatement parametrizado agora

🔥0 | 💰 0 | 🧹 0

**Rodada 2**

Questão Relâmpago:: Opção escolhida: A)

🔥0 | 💰 0 | 🧹 0

**Rodada 3**

Opção escolida:
A) Corrigir o getInstancia do singleton para guardar a instância

🔥 +1 | 💰 5 mil

## Pontuação Final: 🔥 +1 | 💰 R$ 20 mil | 🧹 0

## 🔎 O caminho do MEU grupo (preencher na 3ª aula, quando o mapa for revelado)

Uma linha por decisão registrada acima (usem os títulos ditados em aula):

| #   | Decisão | Nossa letra | Consequência que ELA teria tido |
| --- | ------- | ----------- | ------------------------------- |
|     |         |             |                                 |
|     |         |             |                                 |
|     |         |             |                                 |

_(adicionem linhas conforme as decisões da madrugada)_

---

# 📋 PÓS-MORTEM · relatório de incidente (montar em sala na 3ª aula)

> Rascunho em aula e commit final `pos-mortem:` até 23h59 do dia da 3ª aula.

## 1. Linha do tempo da madrugada

---

---

---

## 2. Causa raiz de 2 incidentes (aula + mecanismo técnico)

**Incidente 1:** ****\*\*****\*\*****\*\*****\_\_\_****\*\*****\*\*****\*\*****

Aula/mecanismo:

---

**Incidente 2:** ****\*\*****\*\*****\*\*****\_\_\_****\*\*****\*\*****\*\*****

Aula/mecanismo:

---

## 3. O que faríamos diferente (2 rodadas + por quê)

---

---

## 4. A maior lição da equipe

---
