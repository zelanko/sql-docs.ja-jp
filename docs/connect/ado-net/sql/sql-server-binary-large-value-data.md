---
title: SQL Server のバイナリ データと大きな値のデータ
description: SQL Server で大きな値のデータを操作する方法について説明します。
ms.date: 08/15/2019
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 17a38bd45a467625be467f5fb01f0e733f7546bc
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920979"
---
# <a name="sql-server-binary-and-large-value-data"></a>SQL Server のバイナリ データと大きな値のデータ

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

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
