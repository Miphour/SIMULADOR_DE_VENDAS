# SIMULADOR_DE_VENDAS
Simula as vendas de um mercado

# Problema
Tenho uma dificuldade. Não consigo resolver um problema se ele não for um… problema.
Digo isso por que preciso montar um portifólio e, como não consigo resolver questões fictícias, não consigo demonstrar que posso resolver problemas reais, logo não recebo problemas reais e o ciclo se retroalimenta.
Voilà!
Temos um problema real então. Paradoxo é o nome.
Preciso criar uma situação que simula um problema real e validar se o resultado está correto, o que transformará esse desafio em dois: programar uma simulação eficiente e aleatória e fazer uma análise correta dos dados gerados.

## Simulador de vendas
Por que fazer um simulador?
Como eu disse, tenho uma questão com dados falsos. E isso por causa das obviedades e alguma falta de motivação que isso me causa. Pra que me esforçar com algo que não tem nada de divertido aguardando do lado de lá? A distribuição normal é… normal; logo sem graça. 

Entrei num brainstorming comigo mesmo pensando nas possibilidades, e fui desenhando um sistema que pudesse simular as vendas de um mercado com viés, com sazonalidade, com alta demanda, etc etc.
Fácil? Não. Desafiador. Particularmente, gosto de desafios.

Numa simplificação, temos o primeiro movimento da seguinte forma:

Jornada de compra

ENTRA NO MERCADO > SELECIONA UM CARRINHO DE COMPRAS > REALIZA O PAGAMENTO > VAI EMBORA

Então para começar, vamos simular que um cliente entra numa loja e seleciona x dentro de n produtos disponíveis:

    produtos      = ['a','b','c','d','e']
    print(random.sample(produtos,3))
    resultado: ['d', 'b', 'c']

Ok, a função de seleção de produtos existe. 
Mas um mercado (espera-se) possui mais produtos, recebe mais clientes que montam cestas com vários produtos, inclusive com repetições e etc; vamos providenciar:
    
    tab_produtos = '/content/LISTA DE PRODUTOS.csv'  
    lista_produtos = pd.read_csv(tab_produtos)
    produtos      = list(lista_produtos['ID'])
    clientes      = 10
    
    for i in range(clientes):
      tamanho_cesta = random.choice(range(len(produtos)))+1
      print(random.choices(produtos,k=tamanho_cesta)) #-> alterei o parâmetro para "choices" para permitir a repetição
        
Isso resulta em 10 listas que são as cestas de compras dos clientes em questão, todas possuindo entre 1 e 500 itens (limitei a quantidade máxima à quantidade de produtos cadastrados por uma questão de legibilidade) e podendo ter itens repetidos. Isso será alterado no futuro para permitir mais itens.
    

