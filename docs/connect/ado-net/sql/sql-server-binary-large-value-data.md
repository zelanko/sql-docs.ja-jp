---
title: SQL Server のバイナリ データと大きな値のデータ
description: SQL Server で大きな値のデータを操作する方法について説明します。
ms.date: 08/15/2019
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: e60f8ce6bc8e7ef05a2de942d8bbc2885095d493
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75251124"
---
# <a name="sql-server-binary-and-large-value-data"></a>SQL Server のバイナリ データと大きな値のデータ

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET をダウンロードする](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

SQL Server では `max` 指定子が導入されました。これにより、`varchar`、`nvarchar`、および `varbinary` データ型の記憶容量が拡張されています。 `varchar(max)`、`nvarchar(max)`、`varbinary(max)` は、総称して*大きな値のデータ型*と呼びます。 大きな値のデータ型を使用すると、最大で 2^31-1 バイトのデータを格納できます。  
  
SQL Server 2008 では、FILESTREAM 属性が導入されています。これはデータ型ではなく、列に定義できる属性であるため、大きな値のデータをデータベースではなくファイル システムに格納できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
[ADO.NET での大きな値 (max) データの変更](modify-large-value-max-data.md)  
大きな値のデータ型を扱う方法について説明します。  
  
[FILESTREAM データ](filestream-data.md)  
FILESTREAM 属性によって SQL Server 2008 に格納されている大きな値のデータを操作する方法について説明します。  
  
## <a name="next-steps"></a>次のステップ
- [SQL Server のデータ型と ADO.NET](sql-server-data-types.md)
- [ADO.NET での SQL Server のデータ操作](sql-server-data-operations.md)
