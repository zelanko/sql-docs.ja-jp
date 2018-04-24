---
title: リモート テーブルのコピー - Parallel Data Warehouse |Microsoft ドキュメント
description: 分析プラットフォーム システム Parallel Data Warehouse でリモート テーブルのコピーを使用します。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 5ed517a471368e4192ad7393a92274424d37f975
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="remote-table-copy"></a>リモート テーブルのコピー
リモート テーブルのコピー機能を使用して、SQL Server PDW のデータベースからテーブルをリモートの (非アプライアンス) SMP SQL Server データベースにコピーする方法について説明します。 SQL Server PDW のハブとスポークのシナリオを有効にするリモート テーブルのコピーを使用します。  
  
## <a name="BasicsPDE"></a>SQL Server PDW のリモート テーブルのコピーを理解します。  
リモート テーブルのコピーを SMP データベース内のテーブルに、SQL SELECT ステートメントの結果をコピーしてハブとスポークのシナリオを有効にする SQL Server PDW の機能です。 使用してリモート テーブルのコピーが開始、 [CREATE リモート TABLE AS SELECT](../t-sql/statements/create-remote-table-as-select-parallel-data-warehouse.md)ステートメントです。  
  
## <a name="BasicsPrerequisites"></a>リモート テーブルのコピーを使用するための要件  
これらの条件が満たされたときに、SQL Server データベースに SQL Server PDW からリモート テーブルのコピーをコピー テーブルを使用できます。  
  
-   転送先データベースは、SQL Server PDW アプライアンスに接続できるアプライアンス内のサーバーに存在しない Microsoft Windows® システムで実行されている Microsoft® SQL Server® のインスタンスである必要があります。 リモートの SQL Server は、イーサネット ネットワーク経由または InfiniBand ネットワークを使用して SQL Server PDW に接続できます。  
  
-   1 つの有効な SQL Server PDW を使用して選択可能なデータをコピーする必要があります[選択](../t-sql/queries/select-transact-sql.md)ステートメントです。  
  
-   転送先サーバーは、非アプライアンス サーバーである必要があります。 データは、このトピックの手順を使用して 1 つのアプライアンスから直接コピーすることはできません。  
  
-   移行先サーバーは、アプライアンスの Infiniband ネットワーク上のすべてのノードにアクセスする必要があります。  
  
## <a name="ConfigureRemote"></a>リモート テーブルのコピーを構成します。  
リモート テーブルのコピーを使用するには、必要がありますを購入して、Windows のサーバーを構成する Windows server で SQL Server を構成して構成する SQL Server PDW です。 これら 3 つの構成手順を実行するのにには、次のリンクを使用します。  
  
1.  [InfiniBand を使用してリモート テーブルのコピーを受信する外部の Windows システムを構成します。](configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband.md)  
  
2.  [リモート テーブルのコピーを受け取る外部 SMP SQL サーバーを構成します。](configure-an-external-smp-sql-server-to-receive-remote-table-copies.md)  
  
3.  [リモート テーブルのコピーの SQL Server PDW を構成します。](configure-sql-server-pdw-for-remote-table-copies.md)  
  
## <a name="PerformRemote"></a>リモート テーブルのコピーを実行します。  
実行するには、リモート テーブルのコピーを使用して、 [CREATE リモート TABLE AS SELECT](../t-sql/statements/create-remote-table-as-select-parallel-data-warehouse.md) SQL ステートメント。 例は、リモート テーブルの作成に関するトピックに含まれています。  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
