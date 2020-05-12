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
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 54c0511faba6648f45ad1614c17e5d262f38d8a4
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832859"
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
 **integer**  
  
## <a name="remarks"></a>解説  
 ティックあたりの時間はコンピューターによって異なります。 オペレーティング システム上の各ティックは、31.25 ミリ秒、または 30 分の 1 (1/30) 秒です。  
  
## <a name="examples"></a>例  
  
```  
SELECT @@TIMETICKS AS 'Time Ticks';  
```  
  
## <a name="see-also"></a>参照  
 [システム統計関数 &#40;Transact-SQL&#41;](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  
