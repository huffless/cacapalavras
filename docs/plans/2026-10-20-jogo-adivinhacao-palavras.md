# PRD — Jogo casual de adivinhação de palavras

- **Status:** rascunho inicial, baseado na pesquisa e nas respostas de descoberta
- **Data:** 2026-10-20
- **Plataforma inicial:** web responsiva, celular e desktop
- **Público inicial:** público geral que gosta de desafios rápidos de palavras

## 1. Visão do produto

Criar um jogo casual em português do Brasil no qual a pessoa descobre uma palavra secreta a partir de uma categoria/tema e do retorno visual sobre as letras de cada palpite. O produto deve oferecer um desafio diário compartilhado, partidas de treino gratuitas e uma experiência rápida, compreensível e fácil de compartilhar.

## 2. Pesquisa e referências

### Padrões observados

| Referência | Mecânica observada | Aprendizado para o produto |
|---|---|---|
| [Wordle — The New York Times](https://www.nytimes.com/games/wordle/index.html) | Adivinhar uma palavra com tentativas limitadas e retorno visual letra a letra; o resultado pode ser compartilhado sem publicar a resposta. | O ciclo simples de palpite, feedback e resultado pode tornar uma rodada curta e fácil de explicar. O compartilhamento deve preservar a solução. |
| [Connections — The New York Times](https://www.nytimes.com/games/connections) | Agrupar palavras que compartilham uma relação; há um novo desafio diário. | Uma categoria ou tema pode ser uma pista fácil de entender, mas ainda permitir interpretação e descoberta. |
| [Strands — The New York Times](https://www.nytimes.com/games/strands) | Encontrar palavras relacionadas em uma grade de letras e descobrir um tema; há um novo desafio diário. | O tema pode dar unidade à rodada. O formato de grade não será adotado no MVP, mas é uma referência para futuras variações. |
| [Wordle — histórico e mecânicas (Wikipedia)](https://en.wikipedia.org/wiki/Wordle) | A retrospectiva relata a escolha de um conjunto de respostas mais familiares, o limite de um desafio diário e a popularização do compartilhamento visual. | Evitar soluções raras ou obscuras, reduzir a carga diária e permitir que a pessoa compare resultados sem revelar a palavra. É uma fonte secundária e histórica, não uma validação quantitativa de mercado. |

### Síntese e implicações

- Combinar uma regra central simples com feedback progressivo torna o jogo fácil de aprender sem remover o desafio.
- A categoria/tema deve orientar, mas não entregar, a resposta.
- O vocabulário precisa ser familiar ao público brasileiro; uma lista ampla de dicionário, sem curadoria, pode tornar palpites dependentes de sorte.
- Um desafio comum por dia favorece comparação entre pessoas. O treino ilimitado deve ficar separado para não diluir essa experiência.
- O compartilhamento deve mostrar o desempenho, não a resposta.
- As referências são usadas para identificar padrões de design; o produto deve ter identidade, conteúdo e implementação próprios.

## 3. Objetivos

1. Permitir que uma pessoa comece uma rodada sem cadastro de pagamento ou instalação do aplicativo.
2. Entregar um desafio diário curto e igual para todas as pessoas naquele dia.
3. Oferecer prática gratuita com escolha de dificuldade.
4. Incentivar retorno e compartilhamento por meio de estatísticas, sequência diária e resultados sem spoiler.
5. Oferecer o arquivo de desafios anteriores como benefício premium de compra única.

## 4. Não objetivos do MVP

- Aplicativos nativos para Android ou iOS.
- Ranking competitivo, partidas entre pessoas ou recursos sociais com contas públicas.
- Monetização por anúncios ou assinatura recorrente.
- Grade de caça-palavras, modo de agrupamento de palavras ou outras mecânicas além do palpite da palavra secreta.
- Localização para outros idiomas.

## 5. Público e necessidades

**Público primário:** pessoas que gostam de desafios rápidos de palavras, sem exigir experiência prévia em jogos de palavras.

**Necessidades principais:**

- Entender a regra e o tema rapidamente.
- Saber quais letras e posições estão corretas após cada tentativa.
- Encontrar palavras reconhecíveis em português do Brasil.
- Jogar em celular ou desktop, comparar o resultado e retornar no dia seguinte.

## 6. Escopo funcional

### 6.1 Desafio diário — P0

- Exibir uma palavra secreta e sua categoria/tema.
- Todas as pessoas recebem a mesma palavra e o mesmo nível no desafio de uma determinada data.
- O nível diário é definido para aquele dia; a pessoa não escolhe o nível do desafio diário.
- O desafio fica disponível na data local definida pelo produto. O fuso horário e o horário de virada ainda precisam ser definidos.
- Permitir um palpite por linha, com comprimento igual ao da resposta e validação contra o vocabulário aceito.
- Após cada palpite incorreto, indicar:
  - letra na posição correta;
  - letra existente na resposta, mas em outra posição;
  - letra ausente da resposta.
- As letras acentuadas devem ser consideradas distintas de suas versões sem acento. Maiúsculas e minúsculas não alteram a validação.
- A pessoa vence ao acertar ou encerra a rodada ao esgotar as tentativas. O resultado final revela a resposta.
- O desafio concluído não pode ser reiniciado para alterar as estatísticas.

### 6.2 Treino — P0

- Disponibilizar partidas de treino ilimitadas gratuitamente.
- Permitir escolher Fácil, Médio ou Difícil antes de cada partida.
- Reutilizar a mecânica de tema, palpite e feedback do desafio diário.
- O treino não altera a sequência nem as estatísticas do desafio diário.
- Regras iniciais de balanceamento:

| Nível | Comprimento da palavra | Tentativas |
|---|---:|---:|
| Fácil | 4–5 letras | 8 |
| Médio | 5 letras | 6 |
| Difícil | 6–7 letras | 5 |

Esses valores são uma primeira hipótese de produto e devem ser validados em testes de usabilidade e balanceamento.

### 6.3 Estatísticas, sequência e compartilhamento — P0

- Exibir estatísticas do desafio diário, incluindo partidas concluídas e taxa de vitória.
- Acompanhar uma sequência de dias jogados.
- Permitir compartilhar o resultado do desafio diário sem incluir a resposta; o resultado deve identificar o nível e o desempenho por tentativa de forma visual e sem spoiler.
- Oferecer uma alternativa caso a API de compartilhamento do dispositivo não esteja disponível (por exemplo, copiar o resultado).
- O formato final de pontuação e as regras exatas de contagem da sequência ainda precisam ser definidos.

### 6.4 Conta e persistência — P0

- Exigir conta para salvar e sincronizar progresso e para gerenciar a compra premium.
- Preservar estatísticas, sequência e estado de desafios concluídos entre sessões e dispositivos autenticados.
- Incluir fluxos de criação de conta, entrada, saída e recuperação de acesso.
- Coletar e reter somente os dados necessários para conta, progresso e compra; definir a política de privacidade e os processos em conformidade com a LGPD antes do lançamento.

### 6.5 Premium — P1

- Manter o desafio diário e o treino ilimitado gratuitos.
- Desbloquear o arquivo de desafios diários anteriores por uma compra única.
- Indicar claramente o conteúdo premium e o preço antes da compra.
- Restaurar o acesso adquirido quando a pessoa entrar em sua conta em outro dispositivo.
- Valor, forma de pagamento, regras de reembolso e escopo temporal do arquivo são decisões pendentes.

## 7. Requisitos de conteúdo e idioma

- Idioma inicial: português do Brasil.
- A acentuação deve ser obrigatória e validada: por exemplo, uma letra acentuada não equivale à mesma letra sem acento.
- A comparação deve ignorar diferenças entre maiúsculas e minúsculas e lidar corretamente com formas Unicode equivalentes da mesma letra acentuada.
- Respostas e palpites devem vir de uma lista curada para o português brasileiro. A política para plurais, flexões verbais, regionalismos, estrangeirismos, nomes próprios e palavras potencialmente ofensivas ainda precisa ser aprovada.
- Cada resposta deve ter uma categoria/tema pertinente e revisada editorialmente.
- A lista de respostas diárias deve evitar repetição e permitir correção editorial antes da publicação.

## 8. Requisitos de UX, acessibilidade e compatibilidade

- Layout responsivo com suporte a teclado físico e teclado virtual no celular.
- Não usar cor como único meio de comunicar o resultado das letras; combinar cor com símbolo, texto acessível ou outro indicador.
- Os estados do tabuleiro devem ser anunciados de forma compreensível para leitores de tela.
- Garantir foco visível, controles utilizáveis por teclado e contraste adequado.
- A interface deve explicar tentativas restantes e o efeito do acento na validação.
- A partida deve continuar após recarregar a página ou retornar ao jogo, respeitando o estado já persistido.

## 9. Regras de feedback a validar

- As cores/indicadores devem ter a mesma semântica em todas as rodadas.
- Para letras repetidas, o feedback não pode indicar mais ocorrências corretas do que existem na resposta; a ordem de contabilização deve ser implementada e testada explicitamente.
- Palpites que não pertençam à lista aceita devem gerar uma mensagem clara e não consumir tentativa.
- A palavra secreta não deve ser exposta no estado da página antes do fim da rodada, inclusive no conteúdo compartilhado.

## 10. Critérios de aceitação do MVP

1. Uma pessoa consegue iniciar o desafio diário em navegador móvel ou desktop e compreender o tema e as regras.
2. Duas contas que abram o desafio na mesma data recebem a mesma resposta, categoria, nível e limite de tentativas.
3. Um palpite válido mostra corretamente letras certas, letras existentes em posição errada e letras ausentes, incluindo casos com letras repetidas e acentos.
4. Um palpite inválido é rejeitado sem consumir tentativa e com explicação visível.
5. O treino oferece partidas ilimitadas gratuitas e respeita os comprimentos e limites definidos para cada nível.
6. Concluir uma partida de treino não altera o progresso diário.
7. O compartilhamento do desafio diário informa o resultado sem revelar a resposta.
8. O progresso diário e a compra premium permanecem associados à conta após entrada em outro dispositivo.
9. Uma pessoa sem premium consegue jogar o desafio diário e treino ilimitado, mas não consegue abrir o arquivo premium.
10. Uma compra única válida libera o arquivo de desafios anteriores na conta compradora.

## 11. Métricas de sucesso a instrumentar

As metas numéricas devem ser definidas após testes com usuários e estimativa de volume. Instrumentar:

- taxa de início e conclusão do desafio diário;
- taxa de vitória e distribuição de tentativas por nível;
- retorno no dia seguinte e retenção semanal;
- uso do treino e do compartilhamento;
- conversão para compra premium e uso do arquivo;
- erros de validação, abandono e problemas de acessibilidade reportados.

## 12. Decisões ainda abertas

1. **Virada do desafio diário:** horário e fuso de referência.
2. **Sequência:** se conta qualquer participação ou apenas vitória; como tratar dias sem jogar e mudanças de fuso.
3. **Vocabulário:** fonte/licença da lista, inclusão de flexões, palavras regionais e política editorial.
4. **Dificuldade diária:** processo editorial para selecionar nível e resposta, além da duração do arquivo disponível após a compra.
5. **Premium:** preço, provedor de pagamento, reembolso e se a compra é válida permanentemente para toda a conta.
6. **Contas:** método de autenticação, dados mínimos, exclusão de conta e estratégia de sincronização.
7. **Metas:** valores-alvo para retenção, conclusão e conversão depois de obter uma linha de base.
8. **Identidade:** nome final, tom de voz e direção visual do jogo.

## 13. Próximos passos recomendados

1. Validar as decisões abertas de conteúdo, pagamento e sequência.
2. Criar protótipo navegável do desafio diário e do treino em celular.
3. Testar compreensão do feedback e percepção de dificuldade com falantes de português brasileiro.
4. Curar e revisar um conjunto inicial de palavras e temas, incluindo testes de acentuação e letras duplicadas.
5. Implementar o MVP e medir os critérios de aceitação antes de expandir os modos.
