---
title: "@@IO_BUSY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@IO_BUSY'
- '@@IO_BUSY_TSQL'
dev_langs: TSQL
helpviewer_keywords:
- ticks [SQL Server]
- I/O [SQL Server], time spent performing operations
- '@@IO_BUSY function'
- output operations [SQL Server]
- input operations [SQL Server]
- time [SQL Server], I/O operations
ms.assetid: 3c26770c-41ae-4e34-8c82-7bef920ffbca
caps.latest.revision: "31"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d42b1961a8e2c4b6feb43f415f43968fbf68fd8a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40iobusy-transact-sql"></a>&#x40;&#x40;IO_BUSY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  時間を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]以降の入力と出力の操作の実行に費やした[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が最後に起動します。 結果は CPU time increment (「ティック」) であり、他のすべての Cpu の累積的なため、実際の経過時間を超える可能性があります。 乗算 @@TIMETICKS (マイクロ秒) に変換します。  
  
> [!NOTE]  
>  に時間が返された場合@CPU_BUSY、または @@IO_BUSY約 49 日の累積 CPU 時間を超える場合、演算オーバーフロー警告が表示されます。 その場合の値を @@CPU_BUSY 、 @@IO_BUSY および @@IDLE 変数が正確ではありません。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
@@IO_BUSY  
```  
  
## <a name="return-types"></a>戻り値の型  
 **整数 (integer)**  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の統計情報をいくつか含むレポートを表示するには、sp_monitor を実行します。  
  
## <a name="examples"></a>使用例  
 次の例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の起動時から現在までの入出力操作時間をミリ秒単位で返します。 算術オーバーフローを避けるためには、値をマイクロ秒単位に変換するときに、例では、値のいずれかに変換、 **float**データ型。  
  
```  
SELECT @@IO_BUSY*@@TIMETICKS AS 'IO microseconds',   
   GETDATE() AS 'as of';  
```  
  
 次に一般的な結果セットを示します。  
  
```  
  
IO microseconds as of                   
--------------- ----------------------  
4552312500      12/5/2006 10:23:00 AM   
```  
  
## <a name="see-also"></a>参照  
 [sys.dm_os_sys_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [@@CPU_BUSY &#40;Transact-SQL&#41;](../../t-sql/functions/cpu-busy-transact-sql.md)   
 [sp_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [システム統計関数 &#40;Transact-SQL&#41;す。](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  
