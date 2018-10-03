---
title: '@@TIMETICKS (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@TIMETICKS_TSQL'
- '@@TIMETICKS'
dev_langs:
- TSQL
helpviewer_keywords:
- ticks [SQL Server]
- '@@TIMETICKS function'
- microseconds per tick [SQL Server]
- time [SQL Server], ticks
- number of microseconds per tick
ms.assetid: 9d036633-837f-4309-9c45-3d9600258018
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d8a1d9a1f3a4e12c790d42ab12de75f96ca1f7c1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47818400"
---
# <a name="x40x40timeticks-transact-sql"></a>&#x40;&#x40;TIMETICKS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  タイマーのティックをミリ秒数で返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
@@TIMETICKS  
```  
  
## <a name="return-types"></a>戻り値の型  
 **整数 (integer)**  
  
## <a name="remarks"></a>Remarks  
 1 ティックあたりの時間は、コンピューターによって異なります。 オペレーティング システムの各ティックは 31.25 ミリ秒 (32 分の 1 秒) です。  
  
## <a name="examples"></a>使用例  
  
```  
SELECT @@TIMETICKS AS 'Time Ticks';  
```  
  
## <a name="see-also"></a>参照  
 [システム統計関数 (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  
