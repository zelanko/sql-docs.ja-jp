---
title: CURRENT_TIMEZONE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/09/2019
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
ms.openlocfilehash: 6c29cfba3f47506cb88860763d6650cfb3ecab7f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68026394"
---
# <a name="currenttimezone-transact-sql"></a>CURRENT_TIMEZONE (Transact-SQL)

[!INCLUDE[tsql-appliesto-ssver15-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssver15-asdb-xxxx-xxx.md)]

この関数では、サーバーまたはインスタンスによって観測されるタイム ゾーンの名前が返されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`CURRENT_TIMEZONE` では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが実行されているコンピューターのオペレーティング システムから戻り値が取得されます。 SQL Database Managed Instance の戻り値は、基盤となるオペレーティング システムのタイム ゾーンではなく、インスタンスの作成時に割り当てられたインスタンス自体のタイム ゾーンに基づきます。
  
> [!NOTE]  
> 単一 SQL データベースおよびプール SQL データベースにおいて、タイム ゾーンは常に UTC に設定され、`CURRENT_TIMEZONE` では UTC タイム ゾーンの名前が返されます。
  
## <a name="syntax"></a>構文  
  
```sql
CURRENT_TIMEZONE ( )  
```
  
## <a name="arguments"></a>引数

この関数は引数を取りません。
  
## <a name="return-type"></a>戻り値の型  

**varchar**
  
## <a name="remarks"></a>Remarks  

`CURRENT_TIMEZONE` は非決定的関数です。 この列を参照するビューと式には、インデックスを付けることができません。
  
## <a name="example"></a>例

返される値には、実際のタイム ゾーンと、サーバーまたはインスタンスの言語設定が反映されることにご注意ください。

```sql
SELECT CURRENT_TIMEZONE();  
/* Returned:  
(UTC+01:00) Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna 
*/
```  
  
## <a name="see-also"></a>参照

[SQL Database Managed Instance のタイム ゾーン](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-timezone)
