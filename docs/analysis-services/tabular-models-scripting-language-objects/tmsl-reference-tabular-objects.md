---
title: "オブジェクトの定義に表形式モデル スクリプト言語 (TMSL) |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 486f0507-cec6-4672-b947-0bb61d1cbc46
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3f69f6b59054b7fb1880757271b290874448373d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="tmsl-reference---tabular-objects"></a>参照の TMSL - 表形式オブジェクト

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  アプリケーションを作成、使用、または表形式データベースを管理または表形式モードで SQL Sever 2016 Analysis Services インスタンスに接続するには、コマンドと JSON 形式でのオブジェクト表現の Tabular Model Scripting Language (TMSL) を使用できます。  
  
 この記事では、SQL Server Management Studio、SQL Server Data Tools (SSDT) および AMO PowerShell によって生成されるスクリプトに使用する TMSL スキーマの主要なオブジェクトを説明します。  
  
 オブジェクトの定義が JSON し、Create、Alter、TMSL コマンドで使用し、削除します。 参照してください[コマンドで表形式モデル スクリプト言語 &#40;TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/tmsl-reference-commands.md)コマンドの一覧についてはします。  
  
## <a name="main-objects"></a>主要オブジェクト  
 次の表は、TMSL スクリプトで最もよく使用されるオブジェクトの一覧を示します。  
  
|||  
|-|-|  
|[データベース オブジェクト & #40 です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md)|同じレベルのモデルに基づく表形式データベース互換性レベル 1200 以上を定義します。|  
|[モデル オブジェクト & #40 です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/model-object-tmsl.md)|互換性レベル 1200 以上で表形式モデルを定義します。|  
|[データ ソース オブジェクト & #40 です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md)|モデルが DirectQuery モードと、モデルを読み込むのインポート中にまたはパススルー クエリを使用するデータ ソースへの接続を定義します。|  
|[Tables オブジェクト & #40 です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md)|モデルのテーブルを指定します。|  
|[パーティション オブジェクト & #40 です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md)|計算テーブルを含む、テーブルの行セットの記憶域を定義します。|  
|[リレーションシップ オブジェクト & #40 です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/relationships-object-tmsl.md)|テーブル間のリレーションシップを定義します。|  
|[ロール オブジェクト & #40 です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)|アクセス許可、メンバーシップ、およびアクセスを制御するセキュリティ フィルターを定義するデータや操作にします。|  
  
## <a name="see-also"></a>参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  

