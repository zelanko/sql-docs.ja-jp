---
title: SQL XML 列の値
description: SQL Server から XML データを取得し、使用する方法について説明します。
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: aa02072e139c2446ae67086ef43668af4403890c
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75244011"
---
# <a name="sql-xml-column-values"></a>SQL XML 列の値

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET をダウンロードする](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

SQL Server では、`xml` データ型をサポートしています。開発者は、<xref:Microsoft.Data.SqlClient.SqlCommand> クラスの標準動作を使用し、この型を含む結果セットを取得できます。 任意の列が (<xref:Microsoft.Data.SqlClient.SqlDataReader> などに) 取得されるように、`xml` 列を取得できますが、列のコンテンツを XML として操作する必要がある場合は、<xref:System.Xml.XmlReader> を使用する必要があります。  
  
## <a name="example"></a>例  
次のコンソール アプリケーションでは、**AdventureWorks** データベースの **Sales.Store** テーブルから 2 行を選択し、この行の `xml` 列を <xref:Microsoft.Data.SqlClient.SqlDataReader> インスタンスに格納します。 行ごとに、<xref:Microsoft.Data.SqlClient.SqlDataReader> の <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlXml%2A> メソッドを使用して `xml` 列の値が読み取られます。 この値は <xref:System.Xml.XmlReader> に格納されます。 コンテンツを <xref:System.Data.SqlTypes.SqlXml> 変数に設定する場合は、<xref:System.Data.IDataRecord.GetValue%2A> メソッドではなく <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlXml%2A> を使用する必要があることに注意してください。<xref:System.Data.IDataRecord.GetValue%2A> は、`xml` 列の値を文字列として返します。  
  
> [!NOTE]
>  **AdventureWorks** サンプル データベースは、既定では SQL Server のインストール時にはインストールされません。 それをインストールするには、SQL Server Setup を実行します。  
  
[!code-csharp [SqlDataReader_GetSqlXml#1](~/../sqlclient/doc/samples/SqlDataReader_GetSqlXml.cs#1)]
  
## <a name="next-steps"></a>次のステップ
- <xref:System.Data.SqlTypes.SqlXml>
- [SQL Server における XML データ](xml-data-sql-server.md)
