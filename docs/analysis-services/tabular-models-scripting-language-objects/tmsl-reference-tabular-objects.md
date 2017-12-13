---
title: "オブジェクトの定義に表形式モデル スクリプト言語 (TMSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/30/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 486f0507-cec6-4672-b947-0bb61d1cbc46
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fcf8b3c47b7663e467ad421a3732f8663320f055
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="tmsl-reference---tabular-objects"></a>参照の TMSL - 表形式オブジェクト
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]アプリケーションを作成、使用、または表形式データベースを管理または表形式モードで SQL Sever 2016 Analysis Services インスタンスに接続するには、コマンドと JSON 形式でのオブジェクト表現の Tabular Model Scripting Language (TMSL) を使用できます。  
  
 この記事では、SQL Server Management Studio、SQL Server Data Tools (SSDT) および AMO PowerShell によって生成されるスクリプトに使用する TMSL スキーマの主要なオブジェクトを説明します。  
  
 オブジェクトの定義が JSON し、Create、Alter、TMSL コマンドで使用し、削除します。 参照してください[コマンドで表形式モデル スクリプト言語 &#40;TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/tmsl-reference-commands.md)コマンドの一覧についてはします。  
  
## <a name="main-objects"></a>主要オブジェクト  
 次の表は、TMSL スクリプトで最もよく使用されるオブジェクトの一覧を示します。  
  
|||  
|-|-|  
|[データベース オブジェクト &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md)|同じレベルのモデルに基づく表形式データベース互換性レベル 1200 以上を定義します。|  
|[モデル オブジェクト &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/model-object-tmsl.md)|互換性レベル 1200 以上で表形式モデルを定義します。|  
|[データ ソース オブジェクト &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md)|モデルが DirectQuery モードと、モデルを読み込むのインポート中にまたはパススルー クエリを使用するデータ ソースへの接続を定義します。|  
|[Tables オブジェクト &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md)|モデルのテーブルを指定します。|  
|[パーティション オブジェクト &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md)|計算テーブルを含む、テーブルの行セットの記憶域を定義します。|  
|[リレーションシップ オブジェクト &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/relationships-object-tmsl.md)|テーブル間のリレーションシップを定義します。|  
|[ロール オブジェクト &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)|アクセス許可、メンバーシップ、およびアクセスを制御するセキュリティ フィルターを定義するデータや操作にします。|  
  
## <a name="see-also"></a>参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
