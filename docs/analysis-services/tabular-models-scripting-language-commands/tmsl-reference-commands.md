---
title: コマンドで表形式モデル スクリプト言語 (TMSL) |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 915e394805dc49ad761da3b5459b6525776ff9e3
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2018
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
  
  
