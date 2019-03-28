---
title: sp_repldone (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_repldone
- sp_repldone_TSQL
helpviewer_keywords:
- sp_repldone
ms.assetid: 045d3cd1-712b-44b7-a56a-c9438d4077b9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8aa102f134d262eb2342e3774c1960f33f8adffc
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58538234"
---
# <a name="sprepldone-transact-sql"></a>sp_repldone (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバーで最後にディストリビュートされたトランザクションを識別するレコードを更新します。 このストアド プロシージャは、パブリッシャー、パブリケーション データベースに対して実行されます。  
  
> [!CAUTION]  
>  実行する場合**sp_repldone**順序や配信されたトランザクションの一貫性を無効にできる、手動でします。 **sp_repldone**サポート プロフェッショナルの経験豊富なレプリケーションのレプリケーションのトラブルシューティングにのみ使用する必要があります。  
  
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
`[ @xactid = ] xactid` 最後に、サーバーの分散トランザクションの最初のレコードのログ シーケンス番号 (LSN) は、します。 *xactid*は**binary (10)**、既定値はありません。  
  
`[ @xact_seqno = ] xact_seqno` 最後に、サーバーの分散トランザクションの最後のレコードの LSN です。 *xact_seqno*は**binary (10)**、既定値はありません。  
  
`[ @numtrans = ] numtrans` 分散トランザクションの数です。 *numtrans*は**int**、既定値はありません。  
  
`[ @time = ] time` (ミリ秒単位) の指定した場合、必要な数のトランザクションの最後のバッチを配布します。 *時間*は**int**、既定値はありません。  
  
`[ @reset = ] reset` リセット状態です。 *リセット*は**int**、既定値はありません。 場合**1**、レプリケートされたすべてのログ内のトランザクションがマークされているディストリビュート済み。 場合**0**、トランザクション ログは、最初のレプリケートされたトランザクションにリセットし、レプリケートされたトランザクションがマークされていないと分散します。 *リセット*場合のみ有効ですが両方*xactid*と*xact_seqno*は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_repldone**はトランザクション レプリケーションで使用します。  
  
 **sp_repldone**ログ読み取りプロセスで配布されたトランザクションを追跡するために使用します。  
  
 **Sp_repldone**、手動でわかりますサーバー (ディストリビューターに送られます)、トランザクションがレプリケートされることです。 次のものとしてマークされたトランザクションを変更することもできますレプリケーションを待機しています。 レプリケートされたトランザクションの一覧で前方または後方を移動することができます。 このトランザクションおよびそれ以前のトランザクションはすべてディストリビュートされたことを示すマークが付きます。  
  
 必要なパラメーター *xactid*と*xact_seqno*を使用して取得できる**sp_repltrans**または**sp_replcmds**します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバー、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_repldone**します。  
  
## <a name="examples"></a>使用例  
 ときに*xactid*が null の場合、 *xact_seqno*が null の場合、および*リセット*は**1**、レプリケートされたすべて、ログ内のトランザクションがマークされているディストリビュート済み。 これは、機能は、レプリケートされたトランザクションがトランザクション ログに無効になっていると、たとえば、ログを切り捨てるときに便利です。  
  
```  
EXEC sp_repldone @xactid = NULL, @xact_segno = NULL, @numtrans = 0,     @time = 0, @reset = 1  
```  
  
> [!CAUTION]  
>  このプロシージャは、レプリケーション保留中のトランザクションが存在する場合は、トランザクション ログの切り捨てを許可する緊急の状況で使用できます。  
  
## <a name="see-also"></a>参照  
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_replflush &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [sp_repltrans &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
