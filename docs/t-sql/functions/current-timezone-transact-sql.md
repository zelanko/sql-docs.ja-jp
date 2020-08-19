---
description: CURRENT_TIMEZONE (Transact-SQL)
title: CURRENT_TIMEZONE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/28/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CURRENT_TIMEZONE
- CURRENT_TIMEZONE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- current time zone [SQL Server]
- current timezone [SQL Server]
- system time zone [SQL Server]
- system timezone [SQL Server]
- functions [SQL Server], time zone
- functions [SQL Server], timezone
- timezone [SQL Server], functions
- time zone [SQL Server], functions
- CURRENT_TIMEZONE function [SQL Server]
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 828004a15fe7c6fb11dbde0e13b02d85e5685947
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88468082"
---
# <a name="current_timezone-transact-sql"></a>CURRENT_TIMEZONE (Transact-SQL)

[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

この関数では、サーバーまたはインスタンスによって観測されるタイム ゾーンの名前が返されます。 SQL Managed Instance の戻り値は、基盤となるオペレーティング システムのタイム ゾーンではなく、インスタンスの作成時に割り当てられたインスタンス自体のタイム ゾーンに基づきます。
  
> [!NOTE]  
> SQL Database において、タイム ゾーンは常に UTC に設定され、`CURRENT_TIMEZONE` では UTC タイム ゾーンの名前が返されます。
  
## <a name="syntax"></a>構文  
  
```sql
CURRENT_TIMEZONE ( )  
```
  
## <a name="arguments"></a>引数

この関数は引数を取りません。
  
## <a name="return-type"></a>戻り値の型  

**varchar**
  
## <a name="remarks"></a>解説  

`CURRENT_TIMEZONE` は非決定的関数です。 この列を参照するビューと式には、インデックスを付けることができません。
  
## <a name="example"></a>例

返される値には、実際のタイム ゾーンと、サーバーまたはインスタンスの言語設定が反映されることにご注意ください。

```sql
SELECT CURRENT_TIMEZONE();  
/* Returned:  
(UTC+01:00) Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna 
*/
```  
  
## <a name="see-also"></a>関連項目

[SQL Managed Instance のタイムゾーン](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-timezone)

[CURRENT_TIMEZONE_ID()](https://docs.microsoft.com/sql/t-sql/functions/current-timezone-id-transact-sql)
