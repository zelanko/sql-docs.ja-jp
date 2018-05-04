---
title: コマンドで表形式モデル スクリプト言語 (TMSL) |Microsoft ドキュメント
ms.date: 05/30/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.custom: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 4eb07192-6f53-4426-830a-d63a945dbcab
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a12ba3199647029fee5bd422000a4adc5ea4e4d6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="tmsl-reference---commands"></a>参照の TMSL - コマンド
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  コマンドは、オブジェクト定義で、表形式モデル スクリプト言語 (TMSL)、表形式モデル データベースに対してを使用して JSON を使った、XMLA エンドポイントで実行できます。   参照してください[オブジェクト定義を表形式モデル スクリプト言語で&#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/tmsl-reference-tabular-objects.md)次のコマンドで使用されるオブジェクトの一覧についてはします。  
  
## <a name="object-operations"></a>オブジェクトの操作  
  
|||  
|-|-|  
|[Alter コマンド&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md)|完全定義を指定せずには、オブジェクトへのインライン変更を行います。|  
|[コマンドを作成して&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md)|その子孫を含む、新しいオブジェクトを作成します。|  
|[CreateOrReplace コマンド&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md)|作成またはオブジェクト定義の一部を置換します。 完全定義を指定する必要があります。|  
|[Delete コマンド&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md)|その子孫を含むオブジェクトを削除します。|  
  
## <a name="data-refresh-operations"></a>データ更新操作  
  
|||  
|-|-|  
|[MergePartitions コマンド&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/mergepartitions-command-tmsl.md)|ソースに対象パーティションをマージし、ターゲットを削除します。|  
|[Refresh コマンド&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md)|データベース、テーブル、またはパーティションを処理します。|  
  
## <a name="scripting"></a>スクリプトの作成  
  
|||  
|-|-|  
|[コマンドのシーケンス&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/sequence-command-tmsl.md)|バッチ処理を順次または並列で|  
  
## <a name="database-management-operations"></a>データベースの管理操作  
  
|||  
|-|-|  
|[Attach コマンド&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/attach-command-tmsl.md)|サーバーにファイルを追加します。|  
|[Detach コマンド&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/detach-command-tmsl.md)|サーバーからファイルを削除します。|  
|[バックアップ コマンド&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/backup-command-tmsl.md)|データベースのバックアップ ファイルを作成します。|  
|[Restore コマンドの&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/restore-command-tmsl.md)|サーバーにデータベースを復元します。|  
|[Synchronize コマンドの&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/synchronize-command-tmsl.md)|Analysis Services データベースを既存の別のデータベースと同期させます。|  
  
## <a name="see-also"></a>参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Analysis Services データ プロバイダーをインストール&#40;AMO、ADOMD.NET、MSOLAP&#41;](../../analysis-services/instances/install-windows/install-analysis-services-data-providers-amo-adomd-net-msolap.md)   
 [Analysis Services での表形式モデルの互換性レベル](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
