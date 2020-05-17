---
title: SQL Server のデータ型と ADO.NET
description: SQL Server データ型を操作する方法と、.NET データ型を操作する方法について説明します。
ms.date: 08/15/2019
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 50a6e158f5678b30028337b70e1da6914038e64a
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "78896539"
---
# <a name="sql-server-data-types-and-adonet"></a>SQL Server のデータ型と ADO.NET

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

SQL Server と .NET は異なる型システムに基づいているため、データ損失の可能性があります。 データの整合性を確保するために、Microsoft SqlClient Data Provider for SQL Server (<xref:Microsoft.Data.SqlClient>) には、SQL Server データを操作するための型指定されたアクセサー メソッドが用意されています。 <xref:System.Data.SqlDbType> クラスの列挙体を使用すると、<xref:Microsoft.Data.SqlClient.SqlParameter> データ型を指定できます。  
  
SQL Server 2008 には、ビジネス ニーズを満たすように設計された新しいデータ型が導入され、日付と時刻、構造化データ、半構造化データ、および非構造化データを操作することができます。 これらは SQL Server 2008 オンライン ブックで説明されています。  
  
アプリケーションで使用できる SQL Server のデータ型は、使用している SQL Server のバージョンによって異なります。 詳細については、SQL Server オンライン ブックの「[データ型 (データベース エンジン)](https://go.microsoft.com/fwlink/?LinkID=107468)」 を参照してください。
  
## <a name="in-this-section"></a>このセクションの内容  
[SqlTypes とデータセット](sqltypes-dataset.md)  
`SqlTypes` 内の `DataSet` に対する新しい型のサポートについて説明します。  
  
[null 値の処理](handle-null-values.md)  
null 値と 3 値ロジックを操作する方法について説明します。  
  
[GUID と uniqueidentifier 値の比較](compare-guid-uniqueidentifier-values.md)  
SQL Server と .NET で GUID および uniqueidentifier 値を操作する方法を示します。  
  
[日付型と時刻型のデータ](date-time-data.md)  
SQL Server 2008 で導入された新しい日付と時刻データ型を使用する方法について説明します。  
  
[大きな UDT](large-udts.md)  
SQL Server 2008 で導入された大きな値の UDT からデータを取得する方法について説明します。  
  
[SQL Server における XML データ](xml-data-sql-server.md)  
SQL Server から取得した XML データを操作する方法について説明します。  
  
## <a name="reference"></a>リファレンス  
<xref:System.Data.DataSet>  
`DataSet` クラスとそのすべてのメンバーについて説明します。  
  
<xref:System.Data.SqlTypes>  
`SqlTypes` 名前空間およびそのすべてのメンバーについて説明します。  
  
<xref:System.Data.SqlDbType>  
`SqlDbType` 列挙体およびそのすべてのメンバーについて説明します。  
  
<xref:System.Data.DbType>  
`DbType` 列挙体およびそのすべてのメンバーについて説明します。  
  
## <a name="next-steps"></a>次のステップ
- [テーブル値パラメーター](table-valued-parameters.md)
- [SQL Server のバイナリ データと大きな値のデータ](sql-server-binary-large-value-data.md)
