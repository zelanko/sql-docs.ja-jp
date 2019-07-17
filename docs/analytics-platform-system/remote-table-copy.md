---
title: リモート テーブル コピー - Parallel Data Warehouse |Microsoft Docs
description: Analytics Platform System Parallel Data Warehouse でのリモート テーブルのコピーを使用します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 28bd5deda25650d36467281ccbffa7b666f4c695
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960205"
---
# <a name="remote-table-copy"></a>リモート テーブルのコピー
(非アプライアンス) のリモート SMP SQL Server データベースに SQL Server PDW のデータベースからテーブルをコピーするリモート テーブル コピー機能を使用する方法について説明します。 SQL Server PDW のハブとスポークのシナリオを有効にするリモート テーブル コピーを使用します。  
  
## <a name="BasicsPDE"></a>SQL Server PDW のリモート テーブルのコピーを理解します。  
リモート テーブルのコピーは、SQL SELECT ステートメントの結果を SMP データベース内のテーブルにコピーしてハブとスポークのシナリオを実現する SQL Server PDW の機能です。 使用して、リモート テーブルのコピーが開始、 [CREATE リモート TABLE AS SELECT](../t-sql/statements/create-remote-table-as-select-parallel-data-warehouse.md)ステートメント。  
  
## <a name="BasicsPrerequisites"></a>リモート テーブルのコピーを使用するための要件  
これらの条件が満たされたときに、SQL Server データベースに SQL Server PDW からリモート テーブル コピーのコピーにテーブルを使用できます。  
  
-   転送先データベースは、SQL Server PDW アプライアンスに接続できるアプライアンス内のサーバーに存在しない Microsoft Windows® システムで実行されている Microsoft® SQL Server® のインスタンスである必要があります。 リモートの SQL Server は、またはイーサネット ネットワーク経由の InfiniBand ネットワークを使用して SQL Server PDW に接続できます。  
  
-   1 つの有効な SQL Server PDW を使用して選択可能なデータをコピーする必要があります[選択](../t-sql/queries/select-transact-sql.md)ステートメント。  
  
-   転送先サーバーは、非アプライアンス サーバーである必要があります。 このトピックの手順を使用して、1 つのアプライアンスから直接データをコピーできません。  
  
-   移行先サーバーは、アプライアンスの Infiniband ネットワーク上のすべてのノードにアクセス可能である必要があります。  
  
## <a name="ConfigureRemote"></a>リモート テーブルのコピーを構成します。  
リモート テーブルのコピーを使用するには、必要がありますを購入して、Windows サーバーを構成する SQL Server、Windows サーバーを構成して SQL Server PDW の構成します。 これら 3 つの構成手順を実行するのにには、次のリンクを使用します。  
  
1.  [InfiniBand を使用してリモート テーブル コピーを受け取るため、外部の Windows システムを構成します。](configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband.md)  
  
2.  [リモート テーブル コピーを受け取るため、外部 SMP SQL サーバーを構成します。](configure-an-external-smp-sql-server-to-receive-remote-table-copies.md)  
  
3.  [リモート テーブル コピー用の SQL Server PDW を構成します。](configure-sql-server-pdw-for-remote-table-copies.md)  
  
## <a name="PerformRemote"></a>リモート テーブル コピーを実行します。  
リモート テーブル コピーを実行するのには、使用、 [CREATE リモート TABLE AS SELECT](../t-sql/statements/create-remote-table-as-select-parallel-data-warehouse.md) SQL ステートメント。 例は、CREATE REMOTE TABLE トピックに含まれています。  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
