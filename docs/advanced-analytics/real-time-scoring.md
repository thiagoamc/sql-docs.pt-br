---
title: "Em tempo real de pontuação | Microsoft Docs"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c4d15a7f605f130ff4f93c7da66ca9a103195c17
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---

# <a name="realtime-scoring"></a>Em tempo real de pontuação

Este tópico descreve um recurso disponível no SQL Server 2016 e no SQL Server 2017 que dá suporte a pontuação em modelos de aprendizado de máquina em tempo quase real.

> [!TIP]
> A pontuação nativo é uma implementação especial em tempo real de pontuação que usa a função de previsão de T-SQL nativa para pontuação muito rápido e está disponível apenas no SQL Server 2017. Para obter mais informações, consulte [pontuação nativo](sql-native-scoring.md).

## <a name="how-realtime-scoring-works"></a>Como funciona a pontuação em tempo real

Em tempo real de pontuação tem suporte no SQL Server 2017 e SQL Server 2016, em tipos de modelo específico criados usando os algoritmos de RevoScaleR ou MicrosoftML Evaluate. Ele usa bibliotecas nativas C++ para gerar pontuações, com base na entrada do usuário fornecida para uma modelo armazenado em um formato binário especial de aprendizado de máquina.

Como um modelo treinado pode ser usado para pontuação sem a necessidade de chamar um tempo de execução de idiomas externos, a sobrecarga de vários processos é reduzida. Isso dá suporte a desempenho muito mais rápido de previsão para cenários de pontuação de produção. Porque os dados nunca saem do SQL Server, os resultados podem ser gerados e inseridos em uma nova tabela sem qualquer conversão de dados entre R e SQL.

Em tempo real de pontuação é um processo de várias etapa:

1. O procedimento armazenado que faz a classificação deve ser habilitado em uma base por banco de dados.
2. Carregar o modelo previamente treinado em formato binário.
3. Você pode fornecer novos dados de entrada, linhas de tabela ou simples, como entrada para o modelo.
4. Para gerar pontuações, chame o sp_rxPredict procedimento armazenado.

## <a name="get-started"></a>Introdução

Para obter exemplos de código e instruções, consulte [como executar pontuação nativo ou em tempo real de pontuação](r/how-to-do-realtime-scoring.md).

Para um exemplo de como pode rxPredict usado para pontuação, consulte [final final empréstimo ChargeOff previsão criados usando o Azure HDInsight Spark Clusters e o serviço do SQL Server 2016 R](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

> [!TIP]
> Se você estiver trabalhando exclusivamente no código de R, você também pode usar o [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) função para pontuação rápida.

## <a name="requirements"></a>Requisitos

Há suporte para a pontuação em tempo real nessas plataformas:

+ Serviços de aprendizado de máquina do SQL Server de 2017 (inclui o Microsoft R Server 9.1.0)
+ SQL Server R Services 2016, com uma atualização da instância do R Services para Microsoft R Server 9.1.0 ou posterior
+ Server (autônomo) de aprendizado de máquina da Microsoft

No SQL Server, você deve ativar em tempo real com antecedência o recurso de pontuação. Isso ocorre porque o recurso requer a instalação de bibliotecas com base em CLR no SQL Server.

Para obter informações sobre em tempo real de pontuação em um ambiente distribuído com base no Microsoft R Server, consulte o [publishService](https://msdn.microsoft.com/microsoft-r/mrsdeploy/packagehelp/publishservice) função disponível no [mrsDeploy pacote](https://msdn.microsoft.com/microsoft-r/mrsdeploy/mrsdeploy), que oferece suporte para Publicando modelos de pontuação, como um novo, um serviço web em execução no servidor de R e em tempo real.

### <a name="restrictions"></a>Restrições

+ O modelo deve ser treinado com antecedência usando um com suporte **rx** algoritmos. Para obter detalhes, consulte [suporte para algoritmos](#bkmk_rt_supported_algos). Em tempo real de pontuação com sp_rxPredict dá suporte a algoritmos de RevoScaleR e MicrosoftML.

+ O modelo deve ser salvo usando a nova função de serialização fornecida no Microsoft R Server 9.1.0. O método de serialização foi otimizado para oferecer suporte a pontuação rápida.

+ Em tempo real de pontuação não usa um interpretador de R; Portanto, qualquer funcionalidade que pode exigir o interpretador R não é suportada durante a etapa de pontuação.  Esses podem incluir:

  + Modelos usando o `rxGlm` ou `rxNaiveBayes` algoritmos não têm suporte no momento

  + Modelos de RevoScaleR que usam uma função de transformação de R, ou uma fórmula que contém uma transformação, como <code>A ~ log(B)</code> não têm suporte em tempo real de pontuação. Para usar um modelo desse tipo, recomendamos que você realize a transformação a para dados de entrada antes de passar os dados para a pontuação em tempo real.

+ Em tempo real de pontuação atualmente é otimizada para previsões rápidas em conjuntos menores de dados, variando de algumas linhas a centenas de milhares de linhas. Em conjuntos de dados muito grandes, a pontuação em R usando rxPredict pode ser mais rápida.

### <a name="a-namebkmkrtsupportedalgosalgorithms-that-support-realtime-scoring"></a><a name="bkmk_rt_supported_algos">Algoritmos que suportam a pontuação em tempo real

+ Modelos de RevoScaleR

  + [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)\*
  + [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)\*
  + [rxBTrees](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)\*
  + [rxDtree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)\*
  + [rxdForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)\*
  
  Modelos marcado com \* também oferecem suporte nativo a pontuação com a função de previsão.

+ Modelos de MicrosoftML

  + [rxFastTrees](https://docs.microsoft.com/r-server/r-reference/microsoftml/rxfasttrees)
  + [rxFastForest](https://docs.microsoft.com/r-server/r-reference/microsoftml/rxfastforest)
  + [rxLogisticRegression](https://docs.microsoft.com/r-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/r-server/r-reference/microsoftml/rxoneclasssvm)
  + [rxNeuralNet](https://docs.microsoft.com/r-server/r-reference/microsoftml/rxneuralnet)
  + [rxFastLinear](https://docs.microsoft.com/r-server/r-reference/microsoftml/rxfastlinear)

+ Transformações fornecidas pelo MicrosoftML

  + [featurizeText](https://docs.microsoft.com/r-server/r-reference/microsoftml/rxfasttrees)
  + [concat](https://docs.microsoft.com/r-server/r-reference/microsoftml/concat)
  + [categóricos](https://docs.microsoft.com/r-server/r-reference/microsoftml/categorical)
  + [categoricalHash](https://docs.microsoft.com/r-server/r-reference/microsoftml/categoricalHash)
  + [selectFeatures](https://docs.microsoft.com/r-server/r-reference/microsoftml/selectFeatures)

### <a name="unsupported-model-types"></a>Tipos de modelo sem suporte

Não há suporte para os seguintes tipos de modelo:

+ Modelos que contém outros tipos de transformações de R sem suporte
+ Modelos usando o `rxGlm` ou `rxNaiveBayes` algoritmos em RevoScaleR
+ Modelos PMML
+ Modelos criados usando outras bibliotecas de R de CRAN ou outros repositórios
+ Modelos que contêm qualquer outro tipo de transformação de R diferente das listadas aqui

### <a name="known-issues"></a>Problemas conhecidos

+ `sp_rxPredict`Retorna uma mensagem de imprecisa quando um valor nulo é passado como o modelo: "System.Data.SqlTypes.SqlNullValueException:Data em Null".

## <a name="next-steps"></a>Próximas etapas

[Como fazer a pontuação em tempo real](r/how-to-do-realtime-scoring.md)