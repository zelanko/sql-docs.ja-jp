---
title: チュートリアル:Python でモデルを構築して顧客を分類する
description: この 4 部構成のチュートリアルシリーズの第 3 部では、SQL Server Machine Learning Services を使用して Python でクラスタリングを実行する K-Means モデルを構築します。
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 08/27/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8707d14b1e332ae6ecebf83213ed53701343bcd3
ms.sourcegitcommit: 26715b4dbef95d99abf2ab7198a00e6e2c550243
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70294407"
---
# <a name="tutorial-build-a-model-in-python-to-categorize-customers-with-sql-server-machine-learning-services"></a>チュートリアル:SQL Server Machine Learning Services で顧客を分類するために、Python でモデルを構築する

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

この 4 部構成のチュートリアルシリーズの第 3 部では、クラスタリングを実行するために、Python で K-Means モデルを構築します。 このシリーズの次のパートでは、SQL Server Machine Learning Services を使用して、このモデルを SQL database にデプロイします。

この記事では、次の方法について説明します。

> [!div class="checklist"]
> * K-Means アルゴリズムのクラスター数を定義します。
> * クラスタリングを実行する
> * 結果の分析

[パート 1](python-clustering-model.md)では、前提条件をインストールし、サンプルデータベースを復元しました。

[パート 2](python-clustering-model-prepare-data.md)では、クラスタリングを実行するために SQL データベースからデータを準備する方法を学習しました。

[パート 4](python-clustering-model-deploy.md)では、新しいデータに基づいて Python でクラスタリングを実行できる SQL データベースにストアドプロシージャを作成する方法について説明します。

## <a name="prerequisites"></a>前提条件

* このチュートリアルのパート3では、[**パート 1**](python-clustering-model.md)の前提条件を満たし、[**パート 2**](python-clustering-model-prepare-data.md)の手順を完了していることを前提としています。

## <a name="define-the-number-of-clusters"></a>クラスターの数を定義する

顧客データをクラスター化するには、 **K-Means** クラスタリングアルゴリズムを使用します。これは、データをグループ化する最も簡単でよく知られている方法の 1 つです。
K-Means の詳細については、[K-Means クラスターアルゴリズムの完全なガイド](https://www.kdnuggets.com/2019/05/guide-k-means-clustering-algorithm.html) を参照してください。

このアルゴリズムでは、次の2つの入力を受け取ります。データ自体、および生成するクラスターの数を表す定義済みの番号 "*k*"。
出力は、クラスター間でパーティション分割された入力データを持つ*k*クラスターです。

K-Means の目標は、項目を k クラスターにグループ化して、同じクラスター内のすべての項目が互いに類似していること、および他のクラスター内の項目とは可能な限り異なるようにすることです。

アルゴリズムで使用するクラスターの数を決定するには、抽出されたクラスターの数によって、グループ内の平方和のプロットを使用します。 使用するクラスターの数は、プロットのベンドまたは "肘" になります。

```python
################################################################################################
## Determine number of clusters using the Elbow method
################################################################################################

cdata = customer_data
K = range(1, 20)
KM = (sk_cluster.KMeans(n_clusters=k).fit(cdata) for k in K)
centroids = (k.cluster_centers_ for k in KM)

D_k = (sci_distance.cdist(cdata, cent, 'euclidean') for cent in centroids)
dist = (np.min(D, axis=1) for D in D_k)
avgWithinSS = [sum(d) / cdata.shape[0] for d in dist]
plt.plot(K, avgWithinSS, 'b*-')
plt.grid(True)
plt.xlabel('Number of clusters')
plt.ylabel('Average within-cluster sum of squares')
plt.title('Elbow for KMeans clustering')
plt.show()
```

![カギ線グラフ](./media/python-tutorial-elbow-graph.png)

グラフに基づいて、 *k = 4*は試してみることをお勧めします。 この*k*値を指定すると、顧客が4つのクラスターにグループ化されます。

## <a name="perform-clustering"></a>クラスタリングを実行する

次の Python スクリプトでは、spark-sklearn パッケージの KMeans 関数を使用します。

```python
################################################################################################
## Perform clustering using Kmeans
################################################################################################

# It looks like k=4 is a good number to use based on the elbow graph.
n_clusters = 4

means_cluster = sk_cluster.KMeans(n_clusters=n_clusters, random_state=111)
columns = ["orderRatio", "itemsRatio", "monetaryRatio", "frequency"]
est = means_cluster.fit(customer_data[columns])
clusters = est.labels_
customer_data['cluster'] = clusters

# Print some data about the clusters:

# For each cluster, count the members.
for c in range(n_clusters):
    cluster_members=customer_data[customer_data['cluster'] == c][:]
    print('Cluster{}(n={}):'.format(c, len(cluster_members)))
    print('-'* 17)
print(customer_data.groupby(['cluster']).mean())
```

## <a name="analyze-the-results"></a>結果の分析

K-Means を使用してクラスタリングを実行したので、次の手順では結果を分析して、実行可能な情報を見つけられるかどうかを確認します。

前のスクリプトから出力されたクラスタリングの平均値とクラスターサイズを確認します。

```results
Cluster0(n=31675):
-------------------
Cluster1(n=4989):
-------------------
Cluster2(n=1):
-------------------
Cluster3(n=671):
-------------------

         customer  orderRatio  itemsRatio  monetaryRatio  frequency
cluster
0        50854.809882    0.000000    0.000000       0.000000   0.000000
1        51332.535779    0.721604    0.453365       0.307721   1.097815
2        57044.000000    1.000000    2.000000     108.719154   1.000000
3        48516.023845    0.136277    0.078346       0.044497   4.271237
```

4つのクラスターは、[パート 1](python-clustering-model-prepare-data.md#separate-customers)で定義されている変数を使用して与えられます。

* *orderRatio* = 返品順序の比率 (部分的または完全に返された注文の総数と注文の合計数)
* *Itemsratio* = 返される項目の比率 (返された項目の合計数と購入した項目の数)
* *Monetaryratio* = 返品金額の比率 (返される品目の合計金額と購入金額の合計金額)
* *frequency* = 返される頻度

K-Means を使用したデータマイニングでは、多くの場合、結果をさらに詳しく分析する必要があります。また、各クラスターについて理解を深めるためにさらに手順を進める必要がありますが、優れた潜在顧客を提供できます
これらの結果を解釈するいくつかの方法を次に示します。

* クラスター0は、アクティブでない (すべての値が0である) 顧客のグループである可能性があります。
* クラスター3は、戻り動作の観点から見たグループであるように見えます。

クラスター0は、アクティブでないことが明らかな顧客のセットです。 場合によっては、このグループに対するマーケティング作業を対象として、購入に関心を出すことができます。 次の手順では、クラスター0の顧客の電子メールアドレスをデータベースに照会して、マーケティング用電子メールを送信できるようにします。

## <a name="clean-up-resources"></a>リソースをクリーンアップする

このチュートリアルを続行しない場合は、SQL Server から tpcxbb_1gb データベースを削除してください。

## <a name="next-steps"></a>次の手順

このチュートリアルシリーズの第3部では、次の手順を完了しました。

* K-Means アルゴリズムのクラスター数を定義します。
* クラスタリングを実行する
* 結果の分析

作成した機械学習モデルをデプロイするには、このチュートリアルシリーズの第4部に従います。

> [!div class="nextstepaction"]
> [チュートリアル: SQL Server Machine Learning Services を使用して Python にクラスターモデルをデプロイする](python-clustering-model-deploy.md)