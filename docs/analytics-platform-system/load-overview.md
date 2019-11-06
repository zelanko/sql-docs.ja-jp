---
title: Parallel Data Warehouse にデータを読み込む |Microsoft Docs
description: 読み込みまたは Integration Services、bcp ユーティリティ、dwloader、または SQL INSERT ステートメントを使用してデータに SQL Server 並列データ ウェアハウス (PDW) を挿入します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: b046839b7c4932b43230d28cc106db1e2ea5d5a7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960693"
---
# <a name="loading-data-into-parallel-data-warehouse"></a>Parallel Data Warehouse にデータを読み込む
読み込みまたは統合サービスを使用してデータを SQL Server 並列データ ウェアハウス (PDW) を挿入[bcp ユーティリティ](../tools/bcp-utility.md)、 **dwloader**コマンド ライン ローダー、または SQL の INSERT ステートメントです。  

## <a name="loading-environment"></a>環境の読み込み  
データを読み込むには、1 つまたは複数のサーバーの読み込みする必要があります。 既存の ETL は、自分または他のサーバーを使用することができますか、新しいサーバーを購入することができます。 詳細については、次を参照してください。[の取得と構成を読み込むサーバー](acquire-and-configure-loading-server.md)します。 この手順では、[サーバー容量計画ワークシートの読み込み](loading-server-capacity-planning-worksheet.md)読み込みに最適なソリューションを計画します。  
  
## <a name="load-with-dwloader"></a>Dwloader を読み込み  
使用して、 [dwloader のコマンドラインのローダー](dwloader.md) PDW にデータを読み込む最も速い方法です。  
  
![読み込みプロセス](media/loading-process.png "読み込みプロセス")  
  
dwloader のでは、コントロールのノードを使用してデータを渡さずに、コンピューティング ノードに直接データを読み込みます。 データを読み込む dwloader は、まず、コンピューティング ノードの連絡先情報を取得するコントロールのノードと通信します。 dwloader のでは、各コンピューティング ノードとの通信チャネルを設定し、コンピューティング ノードにラウンド ロビン方式でデータの 256 KB のチャンクを送信します。  
  
各コンピューティング ノードでは、データ移動サービス (DMS) は、受信し、データのチャンクを処理します。 データの処理には、各行を SQL Server のネイティブ形式に変換して、各行が所属するコンピューティング ノードを確認する配布ハッシュを計算が含まれています。  
  
行を処理した後は、DMS は、各行を適切なコンピューティング ノードと SQL Server のインスタンスに転送するのに shuffle_move を使用します。 に従ってそれらをバッチ処理、SQL Server は、行を受け取ると、 **-b** dwloader でバッチ サイズ パラメーターを設定し、一括は、バッチをロードします。  

## <a name="load-with-prepared-statements"></a>準備されたステートメントを使用して読み込む

準備されたステートメントを使用して、分散され、レプリケートされたテーブルにデータを読み込むことができます。 入力データが対象のデータ型が一致しない場合は、暗黙的な変換が実行されます。 準備されたステートメントの PDW でサポートされている暗黙的な変換は、SQL Server でサポートされる変換のサブセットです。 つまり、変換のサブセットのみがサポートされますが、サポートされる変換は、SQL Server の暗黙的な変換を一致します。 読み込む対象のテーブルが分散またはレプリケートされたテーブルとして定義されるかどうかに関係なく暗黙的な変換が (必要な場合) を対象のテーブル内に存在するすべての列に適用されます。 

<!-- MISSING LINK
For more information, see [Prepared statements](prepared-statements.md).
-->
  
## <a name="related-tasks"></a>Related Tasks  
  
|タスク|説明|  
|--------|---------------|  
|ステージング データベースを作成します。|[ステージング データベースを作成します。](staging-database.md)|  
|Integration Services を使用して読み込みます。|[Integration Services での読み込み](load-with-ssis.md)|  
|Dwloader の型変換をについて説明します。|[dwloader のデータ型の変換規則](dwloader-data-type-conversion-rules.md)|  
|Dwloader のデータを読み込みます。|[dwloader のコマンドラインのローダー](dwloader.md)|  
|挿入に対する型変換をについて説明します。|[INSERT を使用したデータの読み込み](load-with-insert.md)|  
 
<!-- MISSING LINKS
## See Also  
[Grant permissions to load data](grant-permissions-to-load-data.md)  
[Common metadata query examles](metadata-query-examples.md)  
  
-->
