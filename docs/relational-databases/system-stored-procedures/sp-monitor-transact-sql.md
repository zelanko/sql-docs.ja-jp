---
title: "sp_monitor (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_monitor_TSQL
- sp_monitor
dev_langs: TSQL
helpviewer_keywords: sp_monitor
ms.assetid: cb628496-2f9b-40e4-b018-d0831c4cb018
caps.latest.revision: "18"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b61c66570fe3d971f95ebd9f7cce8c26a63937b4
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spmonitor-transact-sql"></a>sp_monitor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  に関する統計情報を表示[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_monitor  
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|Description|  
|-----------------|-----------------|  
|**last_run**|時間**sp_monitor**が最後に実行します。|  
|**current_run**|時間**sp_monitor**が実行されています。|  
|**seconds**|以降の経過秒数**sp_monitor**を実行します。|  
|**cpu_busy**|サーバー コンピューターの CPU が実行されている秒数[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]作業します。|  
|**io_busy**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が入出力操作に費やした秒数|  
|**アイドル状態**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がアイドル状態だった秒数|  
|**packets_received**|入力パケットの数がによって読み取られた[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。|  
|**packets_sent**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が書き込んだ出力パケット数|  
|**@packet_errors**|発生したエラーの数[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パケットを読み書き中にします。|  
|**total_read**|読み取り回数[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。|  
|**total_write**|書き込み回数[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。|  
|**total_errors**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の読み書き中に発生したエラー数|  
|**接続**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] へのログインまたはログイン試行の回数|  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、いくつかの関数によって処理量が追跡されます。 実行する**sp_monitor**これらの関数によって返される現在の値を表示し、プロシージャが実行された最終時刻以降に変更がどの程度を示します。  
  
 各列の統計情報は、フォームで出力*数*(*数*)-*数*% または*数*(*数*). 最初の*数*秒の数を示します (の**cpu_busy**、 **io_busy**、および**アイドル**) または合計数 (他の変数の場合) から[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が再起動されました。 *数*かっこで囲まれた秒数または前回の合計数を指します**sp_monitor**を実行します。 経過時間の割合が割合**sp_monitor**が最後に実行します。 たとえば、レポートには表示**cpu_busy**として 4250 (215) 68% の場合は、CPU がされてから 4250 ビジー状態の秒[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]から 215 の秒数を最後に起動されて**sp_monitor**最後の実行、およびの 68% が、経過時間の合計**sp_monitor**が最後に実行します。  
  
## <a name="permissions"></a>Permissions  
 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のビジー状況に関する情報をレポートします。  
  
```  
USE master  
EXEC sp_monitor  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
||||  
|-|-|-|  
|**last_run**|**current_run**|**seconds**|  
|1998 年 3 月 29 日午前 11:55|1998 年 4 月 4 日午後 2:22|561|  
  
||||  
|-|-|-|  
|**cpu_busy**|**io_busy**|**アイドル状態**|  
|190(0)-0%|187(0)-0%|148(556)-99%|  
  
||||  
|-|-|-|  
|**packets_received**|**packets_sent**|**@packet_errors**|  
|16(1)|20(2)|0(0)|  
  
|||||  
|-|-|-|-|  
|**total_read**|**total_write**|**total_errors**|**接続**|  
|141(0)|54920(127)|0(0)|4(0)|  
  
## <a name="see-also"></a>参照  
 [sp_who &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
