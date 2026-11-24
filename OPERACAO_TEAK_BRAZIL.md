# Operação Comercial Teak Brazil

Manual de trabalho do comercial da Teak Brazil no GHL / Hyak Sales.
Consolidado em 24/11/2026.

Este documento substitui o antigo `OPERACAO_AUTOMACAO_TEAK.md`, que foi perdido
quando o scratchpad da sessão foi limpo em 19/11. Por isso ele mora no
repositório, e não em pasta temporária.

---

## 1. Quem é quem

| | |
|---|---|
| Responsável comercial | Marcelo Carvalho |
| Empresas | Teak Brazil, Nitron, HYAK Internacional |
| Serraria | Ouro Preto do Oeste, Rondônia |
| CD e comercial | Rua Urucuí, 600, Cidade Aracília, Guarulhos SP, 07250-150 |
| Telefone comercial | 11 95150-9821 |
| Madeira | Teca, *Tectona grandis* maciça, de reflorestamento, com FSC |

Somos **fabricantes**, não revenda. Serraria própria e CD próprio. Não temos
representante em nenhuma região e não fazemos instalação.

---

## 2. Regras invioláveis

Estas não se flexibilizam sem ordem direta do Marcelo.

1. **Nunca disparar sem autorização dele.** Mensagem formulada fica parada até
   ele liberar, mesmo que já tenha sido aprovada em versão anterior.
2. **Todo disparo sai por HW, Hyak WhatsApp**, até segunda ordem.
3. **Pedido só é pedido quando está lançado no Sankhya.** Antes disso é
   proposta, por mais adiantada que esteja a conversa.
4. **Desconto até 10%, nunca aplicado sem autorização.** O teto existe como
   conhecimento, não como alçada.
5. **Nunca prometer 100% cerne, sem nó ou sem brancal.** Painel de teca de
   reflorestamento tem brancal, e fornecedor que diz o contrário cria
   devolução.
6. **Nunca dizer ao cliente que a madeira vai acinzentando com o sol.**
7. **Não citar que produzimos madeira serrada de teca e subprodutos 100% cerne.**
8. **Ripado não se oferece.** Só entra na conversa se o lead perguntar.
9. **Nunca afirmar espécie, produto, fornecedor ou segmento de um lead sem
   confirmação direta dele.**
10. **Texto em outro idioma volta sempre com a versão em português junto**, sem
    o Marcelo precisar pedir.

### Estilo de escrita

- **Sem travessão.** Sem dois pontos, com uma exceção: introdução de lista ou
  de anexo ("Seguem as fotos:", "segue abaixo o preço:").
- Fecho padrão para homem: *"Grande abraço meu amigo e qualquer dúvida estou à
  disposição."*
- Fecho para mulher ou gênero desconhecido: *"Grande abraço e qualquer dúvida
  estou à disposição."*
- Quando a mensagem pede decisão, o fecho muda: *"Grande abraço meu amigo e
  fico aguardando o seu ok para avançarmos..."*
- Continuação no mesmo dia não leva saudação nem fecho.

---

## 3. GHL, identificadores fixos

| Item | ID |
|---|---|
| Location | `DRhJc78pTfF9dlaH5NK9` |
| Usuário Marcelo | `nXGAeMtrbxH6b8FKT9OP` |
| Provider HW, disparos do Marcelo | `6aa2d8476548eab979ff881e` |
| Provider Hyak WhatsApp SMS, Nina | `6aa320fd652d120992c7a592` |
| Pipeline Novos Clientes | `7iiNAcXm907KDd85DuZp` |

Estágios do pipeline:

| Estágio | ID |
|---|---|
| Lead | `b7a856ab-509d-459f-9093-80a595950047` |
| Qualificação | `f20fcee2-e250-4873-9f4e-b66e076b9e5d` |
| Proposta | `e5cfd1cb-252c-481c-a0b9-0850cbb68e38` |
| Primeiro Pedido | `1bd8eaa6-b6a8-4cfd-9201-67acd246ae6f` |
| Perdido | `027e2c1c-2b1b-47a5-ae58-f6e29ec4572b` |

### Mecânica de envio

- Operação `send-a-new-message`, com `type: "Custom"`,
  `conversationProviderId` e `message`.
- `scheduledTimestamp` em **segundos UTC**. Cancelamento por
  `cancel-scheduled-message` com o `messageId`.
- Vários anexos cabem **numa única mensagem**, pelo array `attachments`. É
  assim que se economiza disparo.
- URL pública de mídia:
  `https://assets.cdn.filesafe.space/DRhJc78pTfF9dlaH5NK9/media/<id>.<ext>`
  A extensão precisa ser conferida antes, porque varia entre `png`, `jpeg` e
  `pdf` e um erro aí derruba o anexo.

---

## 4. A Nina e a linha compartilhada

A Nina é o autoatendimento. Ela responde cliques de campanha das 8h às 19h, de
segunda a sábado, e para sempre antes de preço, prazo e condição de venda,
passando para o Marcelo.

**A Nina não tem número próprio.** Os dois providers saem pela mesma linha, a
do Marcelo, e as mensagens dela carregam a marca `#contact_instance: Marcelo`.

Consequência prática: **todo volume da Nina consome a mesma cota de WhatsApp
que os nossos disparos.** A conta diária nunca é só o que a gente manda.

---

## 5. Limite de volume no WhatsApp

### O que aconteceu em 16/11/2026

77 mensagens saíram pela linha entre 16h56 e 18h42, sendo 46 de uma grade de 14
leads e 31 de uma reativação. No dia seguinte a conta apareceu restrita, com
contagem regressiva de cerca de 17h30.

O sinal que mais pesou não foi o total, foi a repetição: as 31 da reativação
saíram com **texto literalmente idêntico**, mudando só o primeiro nome, em 90
minutos.

### Regras de volume, política nossa

1. No máximo **20 mensagens iniciadas por nós por dia**, lembrando que a Nina
   já consome parte da cota.
2. No máximo **5 por hora**. Na prática temos operado entre 6 e 7 por hora em
   dias de resposta a conversa aberta, o que é aceitável porque responder pesa
   muito menos que iniciar.
3. **Nunca o mesmo texto literal para mais de 5 contatos.** Em lote de
   reativação, escrever de 3 a 4 variantes e alternar.
4. Espalhar ao longo do dia. Nada de lote concentrado em duas horas.
5. Priorizar sempre quem escreveu por último.
6. Lote grande de reativação vira campanha de vários dias, nunca de uma tarde.

### Em caso de nova restrição

- Não disparar nada pela API enquanto durar.
- Responder só manualmente, pelo celular, em conversa já ativa.
- Não trocar de número no mesmo aparelho para contornar.
- Conferir depois se mensagens agendadas falharam durante a janela, porque o
  lead que escreveu nesse período pode ter ficado sem nenhuma resposta.

### Melhoria estrutural pendente

Separar a linha da Nina da linha comercial. Enquanto dividirem o número,
qualquer pico de campanha consome a cota de negociação.

---

## 6. Como o Marcelo escreve

Lições tiradas de comparar mensagens minhas com as reescritas dele.

1. **Uma desculpa, uma vez, sem drama.** "Houve um atraso, te peço desculpas"
   basta. Autoflagelo prende a conversa no nosso erro.
2. **Não listar o que a foto ou o vídeo já mostram.** Redundância é o que faz
   a mensagem soar robotizada.
3. **Não explicar o que o cliente não perguntou.** Explicação não solicitada
   parece defesa.
4. **Quando a pergunta é a razão da mensagem, faça a pergunta.** Depois da
   culpa assumida, perguntar direto é honesto, não agressivo.
5. **A foto do pacote pronto vale mais que a foto da peça.** Uma prova que o
   produto existe, a outra prova que a nossa parte está feita.
6. **Toda pergunta de condição comercial leva uma saída.** "Se não ficar bom,
   me avisa que vemos outra alternativa." Pergunta fechada sem saída faz o
   cliente sumir em vez de dizer não.
7. **O prazo é do cliente, não nosso.** "Você disse que precisa em janeiro"
   tira o tom de cobrança que "você precisa em janeiro" tem.
8. **Elogiar a operação do cliente.** "Show de bola, volume muito bom",
   "parabéns pela infra".
9. **Explicar por que está perguntando.** "Te pergunto isso pois posso te
   oferecer de duas formas."
10. **Ceder na especificação quando o cliente tem trava real.** Cliente com
    máquina calibrada em 20 mm não muda, então a gente atende em 20 e guarda o
    19 para depois.
11. **Pedir o alvo antes de dar o preço.** Quando o cliente exige preço na
    hora, não recusar: prometer o preço e pedir o target, justificando que se
    quer ser assertivo.
12. **Reticências são a voz dele.** Suavizam sem enfraquecer. Com moderação.
13. **Se um bloco pode sair sem a mensagem perder, ele sai.** Menos blocos
    também significa menos risco para a linha.

---

## 7. Método de abordagem

### Saber o segmento não é motivo para cotar

Mesmo com o segmento confirmado, o caminho é mandar o catálogo e fazer o pedido
de preço partir do lead. A exceção é quando o lead declarou **as duas coisas**,
o que fabrica e o produto exato que procura.

### A pergunta de qualificação certa

Para painel, nunca "é para uma obra sua". A forma correta é:

> Vai ser para usar na sua produção ou para revenda?

"Obra sua" continua válido para deck, forro e assoalho.

### Volume antes de preço

O volume decide a tabela. Uma madeireira entra naturalmente na 183, mas com
volume mensal alto, do tipo 100 peças mês de painel 2200 ou 2500 x 1200, passa
a comprar como grande distribuidor e pode ir para a 182, que é a faixa de
Leroy Merlin e Leo Madeiras.

Perguntar sempre: **quanto por mês, e é pontual ou recorrente?**

### O que muda conforme o estágio

| Estágio | Como a mensagem chama | Bloco extra |
|---|---|---|
| Pedido quase confirmado | "nosso **pedido**" | o que trava a produção |
| Orçamento enviado | "nosso **orçamento**" | nenhum |
| Só amostra, sem cotação | não citar nenhum dos dois | nenhum |

**Nunca chamar de orçamento o que nunca foi cotado.** Conferir no histórico
antes de escrever "nosso orçamento".

### Perfis recorrentes

**Fabricante de utensílio e tábua de churrasco.** Painel longo primeiro,
serrada em segundo plano e só se ele perguntar. Nunca oferecer deck, forro ou
assoalho. Costuma ter CNC router e esquadrejadeira. O gancho forte é o corte na
medida, porque elimina uma etapa da produção dele.

**Madeireira.** Entra na 183, mas não cotar antes de entender o volume. Fechar
pedindo uma call.

**Marcenaria.** Tabela 111.

---

## 8. Tabelas de preço

Arquivo oficial `TABELAS_TEAK_BRAZIL_2026_GHL.xlsx`, media id
`6af70ad4d4ff87db68983953`. Seis abas:

| Tabela | Público |
|---|---|
| 111 | Marcenaria base |
| 182 | Distribuidores e home centers |
| 183 | Revenda |
| 184 | Export FOB, em USD |
| 185 | B2C |
| 186 | Marketplace |

**Colunas que podem ir para o cliente:** REFERÊNCIA, UN., QTD PCT., NOME DO
PRODUTO, PREÇOS. O resto é conhecimento interno.

O fator entre a 111 e a 183 é 0,904.

### Painéis longos de teca, as referências mais usadas

| Ref | Produto | m³/pç | 111 | 183 | 182 |
|---|---|---|---|---|---|
| 721.001.M00 | 1200x2200x18 | 0,04752 | 804,24 | 727,03 | 643,39 |
| 722.001.M00 | 1200x2200x25 | 0,066 | 1.068,17 | 965,62 | 854,53 |
| 723.001.M00 | 1200x2200x30 | 0,0792 | 1.280,99 | 1.158,02 | 1.024,79 |
| 592.001.M00 | FJL 600x2500x18 | 0,027 | 498,69 | 450,81 | 398,95 |
| 636.001.M00 | FJL 1200x2500x18 | 0,054 | 934,05 | 844,38 | 747,24 |
| 637.001.M00 | FJL 1200x2500x25 | 0,075 | 1.272,63 | 1.150,45 | 1.018,10 |
| 638.001.M00 | FJL 600x2500x25 | 0,0375 | 668,04 | 603,91 | 534,43 |
| 624.001.M00 | FJL 1200x2500x30 | 0,09 | 1.514,54 | 1.369,14 | 1.211,63 |
| 593.001.M00 | FJL 600x2500x30 | 0,045 | 788,92 | 713,19 | 631,14 |

### O catálogo é maior do que só painel longo

A planilha tem 16 linhas de produto:

- Painéis curtos, médios e longos em **teca**, **eucalipto** e **pinus**
- **Bancadas**, 630 mm de largura, 30 mm, de 1200 a 2200 mm
- **Ilhas**, 900 mm de largura, 30 mm, de 1600 a 2200 mm
- **Tampos home**, 25 mm, de 300x1200 a 800x2200
- **Tampos redondos**, 25 mm, de 300 a 1200 mm de diâmetro
- **Decks**, **forros** e **assoalhos**

Vale consultar antes de dizer que não temos algo.

### Tampo e painel são a mesma coisa

**Não existe diferença física entre painel e tampo.** É a mesma peça colada, e
o nome muda conforme o uso que o cliente dá. Uma chapa de 2500 x 1200 é painel
para quem vai cortar e é tampo para quem vai usar inteira numa mesa.

O que define o produto é **a medida que o cliente pede**, nunca a palavra que
ele usou.

- Cliente pede **comprimento e largura**, do tipo 70 x 70 cm ou 180 x 80 cm,
  é peça retangular ou quadrada. Sai de painel, cortado na medida, ou da linha
  de **tampos home**, que é 25 mm.
- Cliente pede **diâmetro**, do tipo 300 mm, aí sim é **tampo redondo**, que é
  uma linha própria.

**Erro a não repetir:** ouvir "tampo" e assumir redondo. Sempre conferir as
medidas antes de classificar o pedido.

Lembrando que as linhas de bancada, ilha, tampo home e tampo redondo já são
painel cortado e acabado em medidas prontas. Antes de orçar corte na medida,
vale ver se já não existe uma referência de catálogo que atende.

### Revestimentos, vendidos por m²

Pacote de 10 m² por referência. Largura e espessura são fixas, o comprimento
vem mesclado de 500 a 3000 mm.

| Ref | Produto | 111 | 183 | 182 |
|---|---|---|---|---|
| 641.010.M00 | Deck liso 70 mm, 20 mm esp. | 247,85 | 224,05 | 198,28 |
| 461.010.M00 | Deck liso 90 mm, 20 mm esp. | 225,93 | 204,24 | 180,74 |
| 463.010.M00 | Deck ranhurado 70 mm, 20 mm esp. | 254,16 | 229,76 | 203,33 |
| 464.010.M00 | Deck ranhurado 90 mm, 20 mm esp. | 233,44 | 211,03 | 186,75 |
| 642.010.M00 | Forro 70 mm, **12 mm** esp. | 165,22 | 149,36 | 132,17 |
| 462.010.M00 | Forro 90 mm, **12 mm** esp. | 152,65 | 138,00 | 122,12 |
| 676.010.M00 | Assoalho 70 mm, 20 mm esp. | 247,85 | 224,05 | 198,28 |
| 767.010.M00 | Assoalho 90 mm, 20 mm esp. | 225,93 | 204,24 | 180,74 |

Pontos que importam na conversa:

- **Deck e assoalho têm 20 mm de espessura. Forro tem 12 mm.** Não confundir.
- Deck liso e assoalho têm **preço idêntico** em cada largura. O que diferencia
  é o perfil, não o valor.
- **A régua de 70 mm é mais cara que a de 90 mm em todas as linhas**, e é
  também a de maior saída na serraria. Isso é alavanca: quem aceita 90 mm paga
  menos.
- **Não se fecha pedido em comprimento fixo único.** A quantidade precisa vir
  distribuída em pelo menos três comprimentos.

### Pedido mínimo, texto oficial da planilha

> **Linha painéis:** faturamento mínimo aproximado de R$ 2.500,00 por pedido,
> podendo ser composto com mix de referências e respeitando a quantidade por
> pacote.

> **Linha revestimentos:** faturamento mínimo de 10 m² por referência. A
> largura e a espessura são fixas, com comprimentos mesclados de 500 a
> 3.000 mm.

### Fora de catálogo

A própria planilha abre a porta: medidas, espécies, tipos de colagem, perfis,
acabamentos e **grades de classificação e qualidade** diferentes dos listados
podem ser fornecidos **sob consulta**. Vale usar essa frase quando o lead pedir
algo que não está na tabela, em vez de dar um não seco.

---

## 9. Limites técnicos do produto

- **Espessuras de painel de teca: 18, 25 e 30 mm.** Não existe 20 mm em linha.
  35, 40 mm e acima são produção dedicada, com mínimo de 10 peças por
  espessura.
- Maior chapa: **1200 x 2500 mm**. Também há 1200 x 2200.
- Produzimos **maciça e mosaico**.
- O painel é produzido com sobra: para o nominal 1200 x 2500, sai
  **1210 x 2520**, ou seja 10 mm de folga na largura e 20 mm no comprimento.
- Vendemos painel avulso e **fazemos corte na medida**.

---

## 10. Frete

Texto oficial da planilha:

> **DAP**, endereço do cliente, até 200 km de Guarulhos SP, Incoterms 2020.
> Frete por conta da Teak Brazil. Descarga por conta do cliente.

> **FCA**, fábrica Teak Brazil, Guarulhos SP, Incoterms 2020. Para destinos
> acima de 200 km de Guarulhos SP, frete por conta do cliente.

Na prática:

- Até **200 km do CD de Guarulhos**, o frete pode ser por nossa conta, a partir
  de pedido na faixa de R$ 2.500. Descarga por conta do cliente.
- Acima de 200 km, frete por conta do cliente.
- **DDD não define distância.** Já tivemos DDD 19 a 212 km, fora do raio, e
  outro DDD 19 a 174 km, dentro. Sempre pedir **endereço completo com CEP** ou
  a ficha cadastral.
- Caso especial: ilha, como Ilhabela, depende de balsa e não entra no raio
  normal sem conferir com a transportadora.

### Incoterm, quando citar a sigla

- **Início de negociação:** não citar DAP nem FCA. Dizer apenas que o preço já
  vai com o **frete por nossa conta**, ou que o frete fica por conta do
  cliente, em português claro.
- **Proposta final:** pode usar a sigla, DAP ou FCA com Incoterms 2020, porque
  ali o documento precisa de precisão.
- Quando usar a sigla, sempre seguir com a frase explicada ao lado.
- Conhecimento interno, não se explica ao cliente sem ele perguntar: no mercado
  interno brasileiro, FOB é frete por conta do cliente e CIF por nossa conta.

---

## 11. Corte na medida

**R$ 3,50 por passada**, preço geral, não condição de cliente específico.

### A matemática das passadas

Cada passada divide um retângulo em dois. Portanto:

```
passadas = peças + retângulos de sobra − 1     (por chapa)
```

Ao calcular, descontar **3 mm de serra por passada** e usar a medida real de
produção, 1210 x 2520, não a nominal.

### Exemplo conferido, peça de 300 x 400 mm

**Chapa 638, 600 x 2500 x 25 mm**
12 peças por chapa. 12 passadas. R$ 42,00 de serviço, R$ 3,50 por peça.
Peça pronta na 111: R$ 55,67 de painel mais R$ 3,50 de corte, igual a
**R$ 59,17**.

**Chapa 637, 1200 x 2500 x 25 mm**
24 peças por chapa. 25 passadas. R$ 87,50 de serviço, R$ 3,65 por peça.
Peça pronta na 111: R$ 53,03 de painel mais R$ 3,65 de corte, igual a
**R$ 56,68**.

A chapa maior sai cerca de 4% mais barata por peça. As duas consomem o mesmo
volume de madeira por peça, 0,003125 m³. A diferença vem do preço por m³ de
cada referência.

**Alerta de folga.** Na 637, três colunas de 400 mm consomem 1200 mm mais três
passadas de 3 mm, igual a 1209 mm, contra 1210 disponíveis. **Sobra 1 mm.** Se
a produção precisar refilar a borda, as 24 peças não fecham. Confirmar com a
produção antes de prometer.

---

## 12. Conhecimento técnico de madeira

### Três processos que o cliente confunde

| Processo | O que é |
|---|---|
| **Secagem KD** | Estufa de 40 a 80 °C, tira água, leva a 8 a 12% de umidade. Não altera a estrutura da madeira. É o que fazemos. |
| **Termorretificação** | 180 a 215 °C com pouco oxigênio, degrada hemiceluloses, escurece a peça por inteiro e **tira de 10 a 30% da resistência**. Não fazemos. |
| **Autoclave** | CCA ou CCB injetado sob pressão. Só penetra no alburno e deixa tom esverdeado. A serraria consegue fazer. |

**Autoclave não serve para teca.** O cerne da teca é impermeável e naturalmente
durável, então o produto não penetra e o tratamento não agrega.

### Outros pontos firmados

- Peça quadrada ou redonda de coração centrado racha radialmente na ponta ao
  secar. É característica, não defeito, mas precisa ser dita antes.
- Para teca em exterior: **óleo penetrante com filtro UV e pigmento**, não
  verniz. Selar o topo e aplicar o acabamento na obra, depois de instalado.
- Massa: peça com massa em excesso se descarta. Correção pequena, de no máximo
  1 cm de área, para fechar nó aberto, é aceitável.

---

## 13. Armadilhas operacionais

1. **Texto e anexo na mesma mensagem saem na ordem errada.** O anexo vira o
   conteúdo principal e o texto vira legenda, aparecendo **abaixo**. O texto que
   anuncia vai sempre num bloco próprio, antes, e o anexo num bloco só dele.
2. **Vários anexos cabem numa mensagem só.** É assim que se reduz o número de
   disparos.
3. **O GHL não anexa a assinatura de e-mail em envio por API.** Tem que ir no
   corpo, manualmente.
4. **A Nina não abre imagem.** Quando o lead manda medida por foto, ela avisa
   que não recebeu a informação e deixa recado. Alguém precisa abrir antes de
   orçar.
5. **O scratchpad é apagado em restart de container.** Qualquer coisa que
   precise sobreviver vai para o repositório.
6. **`openpyxl` só existe no `python3.13`**, não no `python3`.
7. **Oportunidade marcando como perdida ao mudar de estágio.** Já aconteceu com
   Dr Thiago e Entre Montes, os dois com negociação viva. Vale investigar a
   automação.

---

## 14. Mídia, ids úteis

| Arquivo | ID |
|---|---|
| Catálogo Teak 2026, português | `6ae22e99d1d68437cf896aaa` |
| Catálogo espanhol | `6ae22eb3ae0d376721b52c8a` |
| Catálogo inglês | `6ae22ec9ce53a65ab25d2de9` |
| Catálogo Nitron, utilidades | `6ae2316f36aa4a07e82fee53` |
| Madeira serrada teca 2026 | `6ae22f0ece53a65ab25d35e8` |
| Tabelas 111 em m³, PDF | `6af20bb0e9d59b97b09adac0` |
| Tabelas 2026 GHL, xlsx | `6af70ad4d4ff87db68983953` |

O catálogo **de painéis e deck** é o `6ae22e99d1d68437cf896aaa`. O
`6ae2316f36aa4a07e82fee53` é o da Nitron, de utilidades, e não serve para lead
de painel.

---

## 15. Estado da carteira em 24/11/2026

Caixa estrelada com **273 conversas**.

### Disparados em 24/11

| Lead | O que foi |
|---|---|
| Edilson Nardes, LUXOR DESIGN | preços de tábua pré-cortada 500x300 em 18, 19 e 20 mm |
| Entre Montes Madeiras | condição especial, 721 a R$ 404,00 a peça, R$ 8.501,68 o m³, frete nosso |
| Lucas Magno | painel com corte em 30x50 e 30x90, rendimento de 20 peças por chapa |
| Eliel Mazzucca | retomada após 7 dias, qualificação |
| Hamilton | 638 cortada em 30x40, R$ 59,17 a peça pronta |

### Prontos e aguardando liberação

Claudemir, Bruno L.Lopes, Ismael Judá, Terci, Cleber Ribeiro, Aparecido e
sergio equatorian.

### Travados

| Lead | O que falta |
|---|---|
| Dr Thiago | resposta do financeiro sobre boleto 30 e 60 dias para pessoa física |
| Mike Mangieri, Novo Building Products | aval para enviar a resposta por e-mail |
| Rafael Santos | abrir as duas imagens com as medidas |
| Robison | conteúdo do anexo |
| Edivaldo | saber o que ele está aguardando |
| Rebeca Barreto | contexto do "Para nós" |
| Silvio Ricardo | conteúdo do anexo |

### Negociações de referência

**Mike Mangieri, Novo Building Products, Lowe's.** Perdemos o programa. Ele
informou que estávamos **10% acima no painel retangular e quadrado e 40% acima
no redondo**, e que teca na Novo só existia nesse programa. Leitura: 10% é
distância de negociação, dentro do nosso teto de desconto. 40% é distância
estrutural, o redondo não compete hoje.

**Oxine, Franca SP.** Constrói chalés, dois em produção. A 400 km, frete por
conta dele. Ligação prevista para quarta 25/11.

**Toro Design, Murilo Deneno.** Interessado em ripado, pediu preço. Pedimos o
target por m² antes de cotar.
