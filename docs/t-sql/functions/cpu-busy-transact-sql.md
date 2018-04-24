---
title: '@@CPU_BUSY (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: da3fd1c4b0e66be485dcf25fdd0b3bdcb0079c6c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="x40x40cpubusy-transact-sql"></a>&#x40;&#x40;CPU_BUSY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が起動してからの動作時間を返します。 結果は CPU 時間の増分 ("ティック") で返され、これはすべての CPU 時間を累積したものです。したがって、実際の経過時間を超える場合があります。 マイクロ秒に変換するには、@@TIMETICKS を乗算します。
  
> [!NOTE]  
>  @@CPU_BUSY または @@IO_BUSY で返される時間が、約 49 日分の累積 CPU 時間を超えた場合は、演算オーバーフロー警告が表示されます。 その場合、@@CPU_BUSY@@IO_BUSY、および @@IDLE の各変数は正確ではありません。  
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```
@@CPU_BUSY  
```  
  
## <a name="return-types"></a>戻り値の型
**整数 (integer)**
  
## <a name="remarks"></a>Remarks  
いくつか含むレポートを表示する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CPU の利用状況などの統計情報の実行 [sp_monitor](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)です。
  
## <a name="examples"></a>使用例  
次の例では、現在のシステム上の日付と時刻における [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CPU 利用状況を示します。 値をマイクロ秒に変換するときに演算オーバーフローが発生しないようにするため、この例では値の 1 つを `float` 型に変換しています。
  
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
[sys.dm_os_sys_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)  
[@@IDLE &#40;Transact-SQL&#41;](../../t-sql/functions/idle-transact-sql.md)  
[@@IO_BUSY &#40;Transact-SQL&#41;](../../t-sql/functions/io-busy-transact-sql.md)  
[sp_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md):  
[システム統計関数 (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/system-statistical-functions-transact-sql.md)
  
  
