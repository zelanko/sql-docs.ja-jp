---
title: "[読み込み]"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.suite: sql
ms.custom: 
ms.technology: mpp-data-warehouse
description: "ロードまたは Integration Services、bcp ユーティリティ、dwloader、または SQL の INSERT ステートメントを使用してデータに SQL Server 並列データ ウェアハウス (PDW) を挿入できます。"
ms.date: 10/20/2016
ms.topic: article
ms.assetid: c7292108-4a48-409e-b0f4-e4ba84dce26f
caps.latest.revision: "22"
ms.openlocfilehash: bef6cf70573aaac642665b9f1e847f4b251e39e9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="load-sql-server-pdw"></a>読み込み (SQL Server PDW)
読み込みまたは Integration Services を使用してデータに SQL Server 並列データ ウェアハウス (PDW) を挿入[bcp ユーティリティ](../tools/bcp-utility.md)、 **dwloader**コマンド ライン ローダー、または SQL の INSERT ステートメントです。  

## <a name="loading-environment"></a>環境の読み込み  
データを読み込むには、1 つまたは複数のサーバーの読み込みが必要です。 新しいサーバーを購入することや、独自の既存の ETL または他のサーバーを使用できます。 詳細については、次を参照してください。[取得および構成を読み込むサーバー](acquire-and-configure-loading-server.md)です。 この手順では、[サーバー容量計画ワークシートの読み込み](loading-server-capacity-planning-worksheet.md)を読み込み中に適したソリューションを計画します。  
  
## <a name="load-with-dwloader"></a>Dwloader による読み込み  
使用して、 [dwloader のコマンド ライン ローダー](dwloader.md) PDW にデータを読み込む方法が最も速くします。  
  
![読み込みプロセス](media/loading-process.png "読み込みプロセス")  
  
dwloader は、[管理] ノードからデータを渡さずに、コンピューティング ノードに直接データを読み込みます。 データを読み込むには、dwloader は、まず、コンピューティング ノードの連絡先情報を取得するコントロールのノードと通信します。 dwloader のでは、各計算ノードとの通信チャネルを設定し、コンピューティング ノードにラウンド ロビン方式で 256 KB のデータのチャンクを送信します。  
  
各コンピューティング ノードでは、データ移動サービス (DM) は、受信し、データのチャンクを処理します。 データの処理には、各行を SQL Server のネイティブ形式に変換して、各行が所属するコンピューティング ノードを判別配布ハッシュを計算が含まれています。  
  
行を処理するには後、は、DMS は、各行を適切なコンピューティング ノードと SQL Server のインスタンスに転送するのに、ランダム再生の移動を使用します。 そのバッチによるとそれらの SQL Server は、行を受け取ると、 **– b** dwloader のバッチ サイズ パラメーターを設定し、次の一括読み込みのバッチ。  

## <a name="load-with-prepared-statements"></a>準備されたステートメントによる読み込み

準備されたステートメントを使用して、分散型とレプリケートされたテーブルにデータを読み込むことができます。 入力データが、対象のデータ型と一致しません、暗黙的な変換が実行されます。 準備されたステートメントの PDW でサポートされている暗黙的な変換は、SQL Server でサポートされる変換のサブセットです。 つまり、変換のサブセットのみがサポートされますが、サポートされる変換は、SQL Server の暗黙的な変換を一致します。 読み込む対象のテーブルが分散またはレプリケートされたテーブルとして定義されるかどうかに関係なく暗黙的な変換が (必要な場合) を対象のテーブルに存在するすべての列に適用されます。 

<!-- MISSING LINK
For more information, see [Prepared statements](prepared-statements.md).
-->
  
## <a name="related-tasks"></a>関連タスク  
  
|タスク|Description|  
|--------|---------------|  
|ステージング データベースを作成します。|[ステージング データベースを作成します。](staging-database.md)|  
|Integration services をロードします。|[Integration Services での読み込み](load-with-ssis.md)|  
|Dwloader の型変換を理解します。|[dwloader のデータ型の変換規則](dwloader-data-type-conversion-rules.md)|  
|Dwloader を使用してデータを読み込みます。|[dwloader のコマンド ライン ローダー](dwloader.md)|  
|INSERT の型変換を理解します。|[INSERT を使用したデータの読み込み](load-with-insert.md)|  
 
<!-- MISSING LINKS
## See Also  
[Grant permissions to load data](grant-permissions-to-load-data.md)  
[Common metadata query examles](metadata-query-examples.md)  
  
-->
