---
title: オブジェクト定義で表形式モデル スクリプト言語 (TMSL) |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: de968c32f8c00132157a5b1b7a6682adc7148446
ms.sourcegitcommit: b75fc8cfb9a8657f883df43a1f9ba1b70f1ac9fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851747"
---
# <a name="tmsl-reference---tabular-objects"></a>TMSL リファレンス - 表形式オブジェクト
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  表形式モードでの SQL Server 2016 Analysis Services インスタンスに接続するか、作成、使用、またはテーブル データベースの管理をアプリケーションでは、コマンドと JSON 形式でオブジェクトの表現、Tabular Model Scripting Language (TMSL) を使用できます。  
  
 この記事では、SQL Server Management Studio、SQL Server Data Tools (SSDT) および AMO PowerShell で生成されたスクリプトで使用する TMSL スキーマの主要なオブジェクトを説明します。  
  
 オブジェクトの定義は JSON では Create、Alter などの TMSL コマンドで使用され、削除します。 参照してください[Tabular Model Scripting Language コマンド&#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-commands/tmsl-reference-commands.md)コマンドの一覧についてはします。  
  
## <a name="main-objects"></a>主要オブジェクト  
 次の表では、TMSL スクリプトで最もよく使用されるオブジェクトの一覧を示します。  
  
|||  
|-|-|  
|[データベース オブジェクト&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md)|同じレベルのモデルに基づく表形式のデータベース互換性レベル 1200 以上を定義します。|  
|[モデル オブジェクト&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/model-object-tmsl.md)|互換性レベル 1200 以上の表形式モデルを定義します。|  
|[データ ソース オブジェクト&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md)|モデルが DirectQuery モードでする際に、モデルを読み込みへのインポート中またはパススルー クエリ用にデータ ソースへの接続を定義します。|  
|[Tables オブジェクト&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md)|モデルのテーブルを指定します。|  
|[パーティション オブジェクト&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md)|計算テーブルを含む、テーブルの行セットの記憶域を定義します。|  
|[リレーションシップ オブジェクト&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/relationships-object-tmsl.md)|テーブル間のリレーションシップを定義します。|  
|[ロール オブジェクト&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)|アクセス許可、メンバーシップ、およびアクセスを制御するセキュリティ フィルターを定義します。 データを操作します。|  
  
## <a name="see-also"></a>参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
