# 📊 Guia Rápido -- Modelo M/M/c

## Elementos

  ----------------------------------------------------------------------------------
  **Elemento**   **O que é**           **Como calcular/definir**     **Exemplo**
  -------------- --------------------- ----------------------------- ---------------
  **λ (lambda)** Taxa de chegada       Conta quantos chegam em certo 120
                 (clientes por unidade período ÷ tempo               clientes/hora →
                 de tempo)                                           λ = 2/min

  **μ (mi)**     Taxa de atendimento   Mede o tempo médio de         1 atendimento
                 de cada servidor      atendimento por cliente → faz leva 2 min → μ
                                       inverso                       = 0,5/min

  **c**          Nº de servidores      Definido pelo sistema ou pelo Banco com 4
                 (atendentes/caixas)   que você quer simular         caixas → c = 4

  **a**          Tráfego oferecido (em a = λ / μ                     λ = 2/min, μ =
                 Erlangs)                                            0,5/min → a = 4

  **ρ (rho)**    Utilização média do   ρ = λ / (c·μ)                 λ = 120/h, μ =
                 sistema                                             30/h, c = 5 → ρ
                                                                     = 0,8 (80%)
  ----------------------------------------------------------------------------------

------------------------------------------------------------------------

## 📐 Fórmulas -- Use dependendo do que o problema pede

  ------------------------------------------------------------------------
  **Se o problema pedir...**       **Você calcula...**      **Fórmula**
  -------------------------------- ------------------------ --------------
  Utilização média dos servidores  ρ                        ρ = λ / (c·μ)

  Probabilidade de esperar na fila P(wait)                  Erlang C:
                                                            P(wait) = \[
                                                            (a\^c / c!) ×
                                                            (c / (c - a))
                                                            \] / \[ Σ
                                                            (a\^n / n!) de
                                                            n=0 até c-1 +
                                                            (a\^c / c!) ×
                                                            (c / (c - a))
                                                            \]

  Tempo médio de espera na fila    Wq                       Wq = P(wait) /
                                                            (cμ - λ)

  Nº médio de clientes na fila     Lq                       Lq = λ · Wq

  Tempo médio no sistema (espera + W                        W = Wq + 1/μ
  atendimento)                                              

  Nº médio de clientes no sistema  L                        L = λ · W

  Verificação de consistência      Lei de Little            L = λ · W e Lq
                                                            = λ · Wq

  Capacidade mínima p/             cmin                     c ≥ λ / μ
  estabilidade                                              
  ------------------------------------------------------------------------

------------------------------------------------------------------------

## 🎯 Interpretação de ρ

-   ρ ≤ 0.7 → sistema confortável (baixa espera).\
-   0.7 \< ρ ≤ 0.8 → eficiente, espera moderada.\
-   0.8 \< ρ ≤ 0.9 → sistema sob pressão.\
-   ρ \> 0.9 → risco de colapso (fila cresce muito).
