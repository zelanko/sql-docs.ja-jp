---
title: "@@IDLE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@IDLE_TSQL'
- '@@IDLE'
dev_langs:
- TSQL
helpviewer_keywords:
- time [SQL Server], idle
- ticks [SQL Server]
- '@@IDLE function'
- status information [SQL Server], idle time
- idle time [SQL Server]
ms.assetid: 8f49c62a-8da5-4afd-a5eb-4df8ef8be755
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: ab308bcb1fd3ffdda8e901b2238111abaddecb81
ms.contentlocale: ja-jp
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40idle-transact-sql"></a>& #x 40; & #x 40 ですアイドル (TRANSACT-SQL)。
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が最後に起動してからアイドル状態になっていた時間を返します。 結果は CPU 時間の増分 ("ティック") で返され、これはすべての CPU 時間を累積したものです。したがって、実際の経過時間を超える場合があります。 乗算@TIMETICKS(マイクロ秒) に変換します。  
  
> [!NOTE]  
>  に時間が返された場合@CPU_BUSY、または @@IO_BUSY約 49 日の累積 CPU 時間を超える場合、演算オーバーフロー警告が表示されます。 その場合の値を @@CPU_BUSY、@@IO_BUSYおよび @@IDLE変数が正確ではありません。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
@@IDLE  
```  
  
## <a name="return-types"></a>戻り値の型  
 **整数 (integer)**  
  
## <a name="remarks"></a>解説  
 いくつか含むレポートを表示する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]実行の統計情報**sp_monitor**です。  
  
## <a name="examples"></a>使用例  
 次の例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の起動時から現在までのアイドル時間をミリ秒単位で返します。 算術オーバーフローを避けるためには、値をマイクロ秒単位に変換するときに、例では、値のいずれかに変換、`float`データ型。  
  
```  
SELECT @@IDLE * CAST(@@TIMETICKS AS float) AS 'Idle microseconds',  
   GETDATE() AS 'as of';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
I  
Idle microseconds  as of                   
----------------- ----------------------  
8199934           12/5/2006 10:23:00 AM   
```  
  
## <a name="see-also"></a>参照  
 [@@CPU_BUSY &#40;Transact-SQL&#41;](../../t-sql/functions/cpu-busy-transact-sql.md)   
 [sp_monitor & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [@@IO_BUSY &#40;Transact-SQL&#41;](../../t-sql/functions/io-busy-transact-sql.md)   
 [システム統計関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  

