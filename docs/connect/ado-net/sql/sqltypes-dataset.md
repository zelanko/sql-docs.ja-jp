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
ms.openlocfilehash: a7ef43ca6afa243e313e8e38bdd05d929161e71f
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75233791"
---
# <a name="sqltypes-and-the-dataset"></a>SqlTypes とデータセット

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET をダウンロードする](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

ADO.NET 2.0 では、<xref:System.Data.SqlTypes> 名前空間を使用して、`DataSet` に対する型のサポートが拡張されました。 <xref:System.Data.SqlTypes> の型は、SQL Server データベースのデータ型と同じセマンティクスおよび精度を持つデータ型を提供することを目的にデザインされています。 <xref:System.Data.SqlTypes> の個々のデータ型には、それに相当する SQL Server のデータ型があり、基本となるデータ表現はいずれも同じです。  
  
<xref:System.Data.DataSet> で <xref:System.Data.SqlTypes> を直接使用すると、SQL Server データ型を操作する際にいくつかの利点があります。 <xref:System.Data.SqlTypes> では、SQL Server ネイティブのデータ型と同じセマンティクスがサポートされています。 <xref:System.Data.DataColumn> の定義で <xref:System.Data.SqlTypes> のいずれかを指定すると、decimal または numeric データ型を共通言語ランタイム (CLR) のデータ型に変換する際に発生する可能性のある精度の損失をなくすことができます。  

次の例では、<xref:System.Data.DataTable> オブジェクトを作成し、CLR データ型の代わりに <xref:System.Data.SqlTypes> を使用して、<xref:System.Data.DataColumn> のデータ型を明示的に定義します。 このコードは、SQL Server の AdventureWorks データベースの Sales.SalesOrderDetail テーブルから取得されたデータを <xref:System.Data.DataTable> に挿入します。 コンソール ウィンドウに表示される出力には、各列のデータ型と、SQL Server から取得された値が示されます。  
  
[!code-csharp[DataWorks DataColumn_DataType#1](~/../sqlclient/doc/samples/DataColumn_DataType.cs#1)]
