---
title: ADO.NET での SQL Server のデータ操作
description: SQL Server でデータを操作する方法について説明します。 一括コピー操作、MARS、非同期操作、およびテーブル値パラメーターに関するセクションがあります。
ms.date: 08/15/2019
ms.assetid: b864ebc9-ed8e-4059-85fd-36d9198f5521
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 3f435e44ef6fb7fb7ff777e2b5361482fcde9a98
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75251114"
---
# <a name="sql-server-data-operations-in-adonet"></a>ADO.NET での SQL Server のデータ操作

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET をダウンロードする](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

このセクションでは、Microsoft SqlClient Data Provider for SQL Server (<xref:Microsoft.Data.SqlClient>) 固有の SQL Server の機能について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
[SQL Server での一括コピー操作](bulk-copy-operations-sql-server.md)  
.NET Data Provider for SQL Server のバルク コピー機能について説明します。  
  
[複数のアクティブな結果セット (MARS)](multiple-active-result-sets-mars.md)  
<xref:Microsoft.Data.SqlClient.SqlDataReader> の各インスタンスが個別のコマンドから起動された場合に、接続で複数の <xref:Microsoft.Data.SqlClient.SqlDataReader> を開く方法について説明します。  
  
[非同期操作](asynchronous-operations.md)  
.NET Framework で使用されている非同期モデルに基づいて設計された API を使用し、非同期データベース操作を実行する方法について説明します。  
  
[テーブル値パラメーター](table-valued-parameters.md)  
SQL Server 2008 で導入されたテーブル値パラメーターを使用する方法について説明します。  
  
## <a name="next-steps"></a>次のステップ
- [SQL Server と ADO.NET](index.md)
