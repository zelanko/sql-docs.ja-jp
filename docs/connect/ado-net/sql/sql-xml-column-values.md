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
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 2704ceae26c58edc85b0cbc1f0fbe6cc98f64311
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80902004"
---
# <a name="sql-xml-column-values"></a>SQL XML 列の値

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

SQL Server では、`xml` データ型をサポートしています。開発者は、<xref:Microsoft.Data.SqlClient.SqlCommand> クラスの標準動作を使用し、この型を含む結果セットを取得できます。 任意の列が (`xml` などに) 取得されるように、<xref:Microsoft.Data.SqlClient.SqlDataReader> 列を取得できますが、列のコンテンツを XML として操作する必要がある場合は、<xref:System.Xml.XmlReader> を使用する必要があります。  
  
## <a name="example"></a>例  
次のコンソール アプリケーションでは、`xml`AdventureWorks**データベースの**Sales.Store**テーブルから 2 行を選択し、この行の** 列を <xref:Microsoft.Data.SqlClient.SqlDataReader> インスタンスに格納します。 行ごとに、`xml` の <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlXml%2A> メソッドを使用して <xref:Microsoft.Data.SqlClient.SqlDataReader> 列の値が読み取られます。 この値は <xref:System.Xml.XmlReader> に格納されます。 コンテンツを <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlXml%2A> 変数に設定する場合は、<xref:System.Data.IDataRecord.GetValue%2A> メソッドではなく <xref:System.Data.SqlTypes.SqlXml> を使用する必要があることに注意してください。<xref:System.Data.IDataRecord.GetValue%2A> は、`xml` 列の値を文字列として返します。  
  
> [!NOTE]
>  **AdventureWorks** サンプル データベースは、既定では SQL Server のインストール時にはインストールされません。 インストールするには、SQL Server Setup を実行します。  
  
[!code-csharp [SqlDataReader_GetSqlXml#1](~/../sqlclient/doc/samples/SqlDataReader_GetSqlXml.cs#1)]
  
## <a name="next-steps"></a>次のステップ
- <xref:System.Data.SqlTypes.SqlXml>
- [SQL Server における XML データ](xml-data-sql-server.md)
