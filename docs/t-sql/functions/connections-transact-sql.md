---
title: '@@CONNECTIONS (Transact-SQL) | Microsoft Docs'
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@CONNECTIONS'
- '@@CONNECTIONS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@CONNECTIONS function'
- connections [SQL Server], number of
- connections [SQL Server], attempted
- number of connection attempts
- attempted connections
ms.assetid: c59836a8-443c-4b9a-8b96-8863ada97ac7
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8422da0d4e550c99fac6c9659f771ab98196cb4a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40connections-transact-sql"></a>&#x40;&#x40;CONNECTIONS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の起動後に、成功または失敗した接続試行数を返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
@@CONNECTIONS  
```  
  
## <a name="return-types"></a>戻り値の型
**整数 (integer)**
  
## <a name="remarks"></a>Remarks  
接続の数はユーザーの数とは異なります。 たとえば、アプリケーションでは、ユーザーの介入なしで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] との間に複数の接続を確立できます。
  
いくつか[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]含むレポートを表示する 実行の接続試行数などの統計情報 **sp_monitor**です。
  
@@MAX_CONNECTIONS は、サーバーに対して同時に許可される接続の最大数です。 @@CONNECTIONS はログインが試行されるたびに増えるため、@@CONNECTIONS は @@MAX_CONNECTIONS よりも大きくなる場合があります。
  
## <a name="examples"></a>使用例  
次の例では、現在のシステム上の日付と時刻におけるログイン試行数を返します。
  
```sql
SELECT GETDATE() AS 'Today''s Date and Time',   
@@CONNECTIONS AS 'Login Attempts';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
  
Today's Date and Time  Login Attempts  
---------------------- --------------  
12/5/2006 10:32:45 AM  211023         
```  
  
## <a name="see-also"></a>参照
[システム統計関数 (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
[sp_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md):
  
  
