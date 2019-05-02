# Spark
Spark Questions

1 - 
Cache é uma técnicas de otimização para cálculos Spark. Está ajuda a salvar resultados para que possam ser reutilizados nos estágios subsequentes de forma mais rápida. Por fim, cache é meramente o persist com o nível de armazenamento MEMORY_ONLY.

2 - 
O Spark é capaz de executar programas até 100x mais rápido que o Hadoop MapReduce na memória, ou 10x mais rápido no disco. O Spark realiza o processamento na memória principal dos Worker Nodes e impede as operações de I/O desnecessárias nos discos. A outra vantagem oferecida pelo Spark é a capacidade de encadear as tarefas, mesmo em um nível de programação do aplicativo, sem gravar ou ou minimizar o número de gravações nos discos.

Uma das principais limitações do MapReduce é que ele mantém o conjunto de dados completo no HDFS após executar cada trabalho. Isso é muito caro porque incorre três vezes (para replicação) o tamanho do conjunto de dados em I/O de disco e uma quantidade semelhante de I/O de rede. No Spark quando a saída precisa ser alimentada em outra operação, os dados são passados diretamente sem serem persistidos.

3 - 
O SparkContext é o portão de entrada da funcionalidade do Apache Spark, a etapa mais importante de qualquer aplicativo do driver Spark é gerar o SparkContext. Ele permite que o seu Aplicativo Spark acesse o Spark Cluster com a ajuda do Gerenciador de Recursos.

4 - 

Os Resilient Distributed Datasets (RDD) é uma coleção distribuída imutável de objetos e cada conjunto de dados no RDD é dividido em partições lógicas somente para leitura, que podem ser calculadas em diferentes nós dos cluster.

Há duas maneiras de criar RDDs: 1 - paralelizar uma coleção existente em seu programa de driver ou 2 - fazer referência a um conjunto de dados em um sistema de armazenamento externo, como um sistema de arquivos compartilhado, HDFS, HBase ou qualquer fonte de dados que ofereça um formato de entrada Hadoop.

Decompondo o RDD:

Resiliente (Resilient): Tolerante a falhas, é capaz de recuperar partições ausentes ou danificadas devido a falhas de nó.

Distribuído (Distributed): Os dados que residem em vários nós em um cluster.

O conjunto de dados (Datasets) é uma coleção de dados particionados com valores primitivos ou valores de valores, por exemplo, tuplas ou outros objetos representando registros de dados. 


5 - 
GroupByKey:
Quando um groupByKey é usado em um RDD, os dados nas partições são embaralhados na rede para formar uma chave e uma lista de valores antes de ser enviado pela rede e isto é uma operação custosa, particularmente quando se está trabalhando em um grande conjunto de dados. 

ReduceByKey
Os dados são primeiramente combinados em cada partição, assim apenas uma saída para uma chave em cada partição é gerada antes de ser enviado pela rede.

Como no ReduceByKey os dados são combinados antes de serem enviados isto faz que o este método seja mais rápido do que o groupByKey.

6 - 
O código descrito no documento é um contador de palavras. 
1 - Um texto é lido e gravado na variável textFile;
2 - Posteriormente  na variável counts é salvo cada palavra no arquvivo de texto lido.
3 - No .map cada é criado para cada palavra um conjunto (chave, valor) sendo o número "1" parâmentro de "valor".
4 - É usado a transformação reduceByKey, agrupando os valores para cada chave distinta.
5 - A saída "counts" e salva em um arquivo de texto no formato (chave, valor) agrupando.

