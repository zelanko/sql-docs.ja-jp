---
title: CURRENT_TIMEZONE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/18/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CURRENT_TIMEZONE)ID
- CURRENT_TIMEZONE_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- current time zone id [SQL Server]
- current timezoneid [SQL Server]
- system time zone id[SQL Server]
- system timezone id[SQL Server]
- functions [SQL Server], time zone id
- functions [SQL Server], timezoneid
- timezoneid [SQL Server], functions
- time zone id [SQL Server], functions
- CURRENT_TIMEZONE_ID function [SQL Server]
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 3cadc9cd33fd1cdabb96cf450ad09253fdd435d1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85684620"
---
# <a name="current_timezone_id-transact-sql"></a>CURRENT_TIMEZONE_ID (Transact-SQL)

[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

この関数では、サーバーまたはインスタンスによって観測されるタイム ゾーンの ID が返されます。 Azure SQL Managed Instance の戻り値は、基盤となるオペレーティング システムのタイム ゾーンではなく、インスタンスの作成時に割り当てられたインスタンス自体のタイム ゾーンに基づきます。
  
> [!NOTE]  
> 単一 SQL データベースおよびプール SQL データベースにおいて、タイム ゾーンは常に UTC に設定され、`CURRENT_TIMEZONE_ID` では UTC タイム ゾーンの ID が返されます。
  
## <a name="syntax"></a>構文  
  
```sql
CURRENT_TIMEZONE_ID ( )  
```
  
## <a name="arguments"></a>引数

この関数は引数を取りません。
  
## <a name="return-type"></a>戻り値の型  

**varchar**
  
## <a name="remarks"></a>解説  

`CURRENT_TIMEZONE_ID` は非決定的関数です。 この列を参照するビューと式には、インデックスを付けることができません。
  
## <a name="example"></a>例

返される値には、実際のタイム ゾーンと、サーバーまたはインスタンスの言語設定が反映されます。

```sql
SELECT CURRENT_TIMEZONE_ID();  
/* Returned:  
W. Europe Standard Time
*/
```  
  
## <a name="see-also"></a>関連項目

[SQL Database Managed Instance のタイム ゾーン](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-timezone)

[CURRENT_TIMEZONE()](https://docs.microsoft.com/sql/t-sql/functions/current-timezone-transact-sql)
