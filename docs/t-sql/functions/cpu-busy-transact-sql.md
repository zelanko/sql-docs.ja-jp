---
title: "@@CPU_BUSY (TRANSACT-SQL) |Microsoft ドキュメント"
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
- '@@CPU_BUSY_TSQL'
- '@@CPU_BUSY'
dev_langs:
- TSQL
helpviewer_keywords:
- CPU [SQL Server]
- status information [SQL Server], CPU
- ticks [SQL Server]
- time [SQL Server], CPU activity
- '@@CPU_BUSY function'
- statistical information [SQL Server], CPU
- CPU [SQL Server], activity
ms.assetid: 81ae0e64-79fa-4a74-9aa5-37045c4cd211
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 80c1228faeaaa4012afc0fd27992a2f5cf389f6e
ms.openlocfilehash: 9263eac53d78da42752704019d95e72431eabcc0
ms.contentlocale: ja-jp
ms.lasthandoff: 10/12/2017

---
# <a name="x40x40cpubusy-transact-sql"></a>&#x40;&#x40;です。CPU_BUSY (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

時間を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が前回起動されてからの作業に費やしたします。 結果は、CPU 時間単位、または「チックで」し、は、他のすべての Cpu の累積なので、実際の経過時間を超える可能性があります。 乗算 @@TIMETICKS (マイクロ秒) に変換します。
  
> [!NOTE]  
>  に時間が返された場合 @@CPU_BUSY または @@IO_BUSY 約 49 日の累積 CPU 時間を超える場合、演算オーバーフロー警告が表示されます。 その場合の値を @@CPU_BUSY 、 @@IO_BUSY および @@IDLE 変数が正確ではありません。  
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```
@@CPU_BUSY  
```  
  
## <a name="return-types"></a>戻り値の型
**整数 (integer)**
  
## <a name="remarks"></a>解説  
いくつか含むレポートを表示する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]CPU 利用状況などの統計情報の実行[sp_monitor](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)です。
  
## <a name="examples"></a>使用例  
次の例では、現在のシステム上の日付と時刻における [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CPU 利用状況を示します。 算術オーバーフローを避けるためには、値をマイクロ秒単位に変換するときに、例では、値のいずれかに変換、`float`データ型。
  
```sql
SELECT @@CPU_BUSY * CAST(@@TIMETICKS AS float) AS 'CPU microseconds',   
   GETDATE() AS 'As of' ;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
CPU microseconds As of
---------------- -----------------------
18406250         2006-12-05 17:00:50.600
```
  
## <a name="see-also"></a>参照
[sys.dm_os_sys_info &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)  
[@@IDLE &#40;Transact-SQL&#41;](../../t-sql/functions/idle-transact-sql.md)  
[@@IO_BUSY &#40;Transact-SQL&#41;](../../t-sql/functions/io-busy-transact-sql.md)  
[sp_monitor &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)  
[システム統計関数 &#40;です。TRANSACT-SQL と&#41;です。](../../t-sql/functions/system-statistical-functions-transact-sql.md)
  
  

