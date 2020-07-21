---
title: 複数の一括コピー操作
description: SqlBulkCopy クラスを使用して SQL Server のインスタンスへのデータの複数の一括コピー操作を実行する方法について説明します。
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: a0a1f24970801698eedc8971f0db54bd08589945
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924294"
---
# <a name="multiple-bulk-copy-operations"></a>複数の一括コピー操作

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

<xref:Microsoft.Data.SqlClient.SqlBulkCopy> クラスの単一のインスタンスを使用して、一括コピー操作を複数回実行できます。 コピー元とコピー先で操作パラメーターが変わる場合 (たとえば、コピー先のテーブル名など)、**WriteToServer** メソッドを続けて呼び出す前に、次の例で示すようにパラメーターを更新する必要があります。 明示的に変更した場合を除き、すべてのプロパティ値は、任意のインスタンスに対して前回一括コピー操作を実行したときと同じ状態のままになっています。  
  
> [!NOTE]
>  通常、一括コピー操作を複数回実行する場合は、同じ <xref:Microsoft.Data.SqlClient.SqlBulkCopy> のインスタンスを使用する方が各操作ごとに別のインスタンスを使用するよりも効率的です。  
  
同じ <xref:Microsoft.Data.SqlClient.SqlBulkCopy> オブジェクトを使用して一括コピー操作を複数回実行する場合、コピー元またはコピー先の情報が各操作ごとに一致しているか異なっているかに関する制限はありません。 ただし、サーバーに書き込み処理を行うときは、列の関連付け情報を毎回正しく設定する必要があります。  

## <a name="example"></a>例

> [!IMPORTANT]
>  このサンプルは、「[一括コピーのセットアップ例](bulk-copy-example-setup.md)」で説明しているように作業テーブルを作成して取得してからでないと動作しません。 このコードでは、**SqlBulkCopy** だけを使用した構文について説明します。 コピー元およびコピー先のテーブルが同一の SQL Server インスタンス内に存在する場合、Transact-SQL `INSERT … SELECT` ステートメントを使用すれば簡単かつ高速にデータをコピーすることができます。  
  
[!code-csharp[DataWorks SqlBulkCopy_._ColumnMappingOrdersDetails#1](~/../sqlclient/doc/samples/SqlBulkCopy_ColumnMappingOrdersDetails.cs#1)]
  
## <a name="next-steps"></a>次のステップ
- [SQL Server での一括コピー操作](bulk-copy-operations-sql-server.md)
