---
title: "sp_repldone (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_repldone
- sp_repldone_TSQL
helpviewer_keywords: sp_repldone
ms.assetid: 045d3cd1-712b-44b7-a56a-c9438d4077b9
caps.latest.revision: "19"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a79d69737292d47b1f896eaf24e5f43a4cc27c30
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sprepldone-transact-sql"></a>sp_repldone (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバーで最後にディストリビュートされたトランザクションを識別するレコードを更新します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
> [!CAUTION]  
>  実行する場合**sp_repldone**順序や配信されたトランザクションの一貫性を無効にできる、手動でします。 **sp_repldone**プロフェッショナル経験豊富なレプリケーションのサポートの指示に従って、レプリケーションのトラブルシューティングにのみ使用する必要があります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_repldone [ @xactid= ] xactid   
        , [ @xact_seqno= ] xact_seqno   
    [ , [ @numtrans= ] numtrans ]   
    [ , [ @time= ] time   
    [ , [ @reset= ] reset ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@xactid=**] *xactid*  
 サーバーの最後の分散トランザクションの最初のレコードのログ シーケンス番号 (LSN) は、します。 *xactid*は**binary (10)**、既定値はありません。  
  
 [  **@xact_seqno=**] *xact_seqno*  
 サーバーの最後の分散トランザクションの最後のレコードの LSN です。 *xact_seqno*は**binary (10)**、既定値はありません。  
  
 [  **@numtrans=**] *numtrans*  
 分散トランザクションの数です。 *numtrans*は**int**、既定値はありません。  
  
 [  **@time=**]*時間*  
 最後のトランザクション バッチをディストリビュートするのに必要な時間をミリ秒単位の数で指定できます。 *時間*は**int**、既定値はありません。  
  
 [  **@reset=**]*リセット*  
 リセットの状態を指定します。 *リセット*は**int**、既定値はありません。 場合**1**、レプリケートされたすべてのログ内のトランザクションがマークされているディストリビュート済みです。 場合**0**トランザクション ログが最初にレプリケートされたトランザクションにリセットされ、レプリケートされたトランザクションがマークされていない、ディストリビュート済みです。 *リセット*場合にのみ有効では両方*xactid*と*xact_seqno* null です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_repldone**トランザクション レプリケーションで使用します。  
  
 **sp_repldone**ログ読み取りプロセスで配布されたトランザクションを追跡するために使用します。  
  
 **Sp_repldone**、手動でわかるサーバー (ディストリビューターに送られます)、トランザクションがレプリケートされることです。 また、レプリケーション待ちの次のトランザクションであることを示すマークが付いたトランザクションを変更できます。 レプリケートされたトランザクションの一覧内では、前後に移動できます。 このトランザクションおよびそれ以前のトランザクションはすべてディストリビュートされたことを示すマークが付きます。  
  
 必要なパラメーター *xactid*と*xact_seqno*を使用して取得できる**sp_repltrans**または**sp_replcmds**です。  
  
## <a name="permissions"></a>Permissions  
 メンバー、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_repldone**です。  
  
## <a name="examples"></a>使用例  
 ときに*xactid*が NULL の場合、 *xact_seqno*が NULL の場合、および*リセット*は**1**、レプリケートされたすべて、ログ内のトランザクションがマークされているディストリビュート済みです。 たとえば次のように、トランザクション ログ内のレプリケートされたトランザクションで無効になったものがあり、ログを切り詰めたい場合に便利です。  
  
```  
EXEC sp_repldone @xactid = NULL, @xact_segno = NULL, @numtrans = 0,     @time = 0, @reset = 1  
```  
  
> [!CAUTION]  
>  このプロシージャは、レプリケーションが保留されているトランザクションがあるときにトランザクション ログの切り詰めを可能にする必要がある場合など、緊急時に使用できます。  
  
## <a name="see-also"></a>参照  
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_replflush &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [sp_repltrans &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
