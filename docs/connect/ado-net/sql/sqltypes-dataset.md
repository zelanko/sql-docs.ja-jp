---
title: SqlTypes とデータセット
description: データセットでの SqlTypes の型サポートについて説明します。
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 0a75aca978847a4e1e54f4933bd6ec7fe708a4e3
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "78896212"
---
# <a name="sqltypes-and-the-dataset"></a>SqlTypes とデータセット

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

ADO.NET 2.0 では、`DataSet` 名前空間を使用して、<xref:System.Data.SqlTypes> に対する型のサポートが拡張されました。 <xref:System.Data.SqlTypes> の型は、SQL Server データベースのデータ型と同じセマンティクスおよび精度を持つデータ型を提供することを目的にデザインされています。 <xref:System.Data.SqlTypes> の個々のデータ型には、それに相当する SQL Server のデータ型があり、基本となるデータ表現はいずれも同じです。  
  
<xref:System.Data.SqlTypes> で <xref:System.Data.DataSet> を直接使用すると、SQL Server データ型を操作する際にいくつかの利点があります。 <xref:System.Data.SqlTypes> では、SQL Server ネイティブのデータ型と同じセマンティクスがサポートされています。 <xref:System.Data.SqlTypes> の定義で <xref:System.Data.DataColumn> のいずれかを指定すると、decimal または numeric データ型を共通言語ランタイム (CLR) のデータ型に変換する際に発生する可能性のある精度の損失をなくすことができます。  

次の例では、<xref:System.Data.DataTable> オブジェクトを作成し、CLR データ型の代わりに <xref:System.Data.DataColumn> を使用して、<xref:System.Data.SqlTypes> のデータ型を明示的に定義します。 このコードは、SQL Server の AdventureWorks データベースの Sales.SalesOrderDetail テーブルから取得されたデータを <xref:System.Data.DataTable> に挿入します。 コンソール ウィンドウに表示される出力には、各列のデータ型と、SQL Server から取得された値が示されます。  
  
[!code-csharp[DataWorks DataColumn_DataType#1](~/../sqlclient/doc/samples/DataColumn_DataType.cs#1)]
