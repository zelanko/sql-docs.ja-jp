---
title: データ マイニングの監視する SQL Server Profiler を使用して |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4ba9720f87cd41849cc118482ffbf4731049e8c9
ms.sourcegitcommit: 4182a1e8be69373dde2fe778f19cab9cd78e447c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51818498"
---
# <a name="using-sql-server-profiler-to-monitor-data-mining-analysis-services---data-mining"></a>SQL Server Profiler を使用したデータ マイニングの監視 (Analysis Services - データ マイニング)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  必要な権限があれば、SQL Server Profiler を使用して、SQL Server Analysis Services のインスタンスに要求として送信されるデータ マイニング操作を監視できます。 データ マイニング操作には、モデルまたは構造の処理、予測クエリまたはコンテンツ クエリ、新しいモデルまたは構造の作成を組み込むことができます。  
  
 すべての操作で SQL Server Analysis Services の同じインスタンスが使用されている限り、SQL Server Profiler は同じ **トレース** を使用して、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]、SQL Server Management Studio、Web サービス、Excel 用データ マイニング アドインなど、複数のクライアントから送信される要求を監視します。 監視対象とする SQL Server Analysis Services のインスタンスごとに個別のトレースを作成する必要があります。 トレースについての全般的な情報と SQL Server Profiler の使用方法については、「[SQL Server Profiler を使用した Analysis Services の監視](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md)」を参照してください。  
  
 キャプチャするイベントの種類に関する特定の指針については、「[再生用のプロファイラー トレースの作成 (Analysis Services)](../../analysis-services/instances/create-profiler-traces-for-replay-analysis-services.md)」を参照してください。  
  
## <a name="using-traces-to-monitor-data-mining"></a>トレースによるデータ マイニングの監視  
 トレースに情報をキャプチャする際に、情報をファイルに保存するか、SQL Server のインスタンス上のテーブルに保存するかを指定できます。 データの格納に使用するメソッドに関係なく、SQL Server Profiler によってトレースを表示し、イベントごとにフィルター処理できます。 次の表に、データ マイニングに必要となる既定の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] トレース内のイベントとサブクラスの一部を挙げます。  
  
|EventClass|EventSubclass|説明|  
|----------------|-------------------|-----------------|  
|**Query Begin**<br /><br /> **クエリの終了**|**0 - MDXQuery**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ストアド プロシージャのすべての呼び出しのテキストを格納します。|  
|**Query Begin**<br /><br /> **クエリの終了**|**1 - DMXQuery**|データ マイニング拡張機能 (DMX) ステートメントのテキストおよび結果が格納されます。|  
|**Progress Report Begin**<br /><br /> **Progress Report End**|**34 - DataMiningProgress**|データ マイニング アルゴリズムの進行状況の情報を出力します。たとえば、クラスター モデルを作成する場合に、進行状況のメッセージによって、作成中である候補のクラスターが通知されます。|  
|**Query Begin**<br /><br /> **クエリの終了**|EXECUTESQL|実行されている Transact-SQL クエリのテキストが格納されます。|  
|**Query Begin**<br /><br /> **クエリの終了**|**2- SQLQuery**|スキーマ行セットに対するクエリのテキストがシステム テーブルの形式で格納されます。|  
|**Discover Begin**<br /><br /> **Discover End**|複数|XMLA にカプセル化された、DMX 関数呼び出しまたは DISCOVER ステートメントのテキストが格納されます。|  
|**[エラー]**|(なし)|サーバーがクライアントに送信したエラーのテキストを格納します。<br /><br /> 「 **エラー (データ マイニング):** 」または「 **情報 (データ マイニング):** 」で始まるエラー メッセージが、DMX 要求への応答として個別に生成されます。 ただし、このようなエラー メッセージを確認するだけでは不十分です。 パーサーが生成するエラーなど、このプレフィックスが付かないその他のエラーの場合でも、データ マイニングに関連していることがあります。|  
  
 トレース ログにコマンド ステートメントを表示することによって、システム ストアド プロシージャの呼び出しなど、クライアントから [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーに送信される複雑なステートメントの構文を参照することもできます。 この情報は、デバッグに利用できます。また、有効なステートメントをテンプレートとして使用し、新しい予測クエリまたはモデルを作成できます。 トレースによってキャプチャできるストアド プロシージャ呼び出しの例については、「 [クラスタリング モデルのクエリ例](../../analysis-services/data-mining/clustering-model-query-examples.md)」を参照してください。  
  
## <a name="see-also"></a>参照  

 [SQL Server 拡張イベントを使用した Analysis Services の監視](../../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md)  
  
  
