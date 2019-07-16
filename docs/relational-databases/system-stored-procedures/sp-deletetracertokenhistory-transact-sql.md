---
title: sp_deletetracertokenhistory (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_deletetracertokenhistory
- sp_deletetracertokenhistory_TSQL
helpviewer_keywords:
- sp_deletetracertokenhistory
ms.assetid: 9ae1be14-0d2f-40b1-9d6e-22d79726abf4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0a7f70f5cd56867add98150d471d61cbc70faad0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68111919"
---
# <a name="spdeletetracertokenhistory-transact-sql"></a>sp_deletetracertokenhistory (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

トレーサー トークン レコードを削除、 [MStracer_tokens &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md)と[MStracer_history &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/mstracer-history-transact-sql.md)システム テーブル。 このストアド プロシージャは、パブリケーション データベースに対して、パブリッシャーまたはディストリビューターのディストリビューション データベースで実行されます。

![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## <a name="syntax"></a>構文

```
sp_deletetracertokenhistory [ @publication = ] 'publication'
    [ , [ @tracer_id = ] tracer_id ]
    [ , [ @cutoff_date = ] cutoff_date ]
    [ , [ @publisher = ] 'publisher' ]
    [ , [ @publisher_db = ] 'publisher_db' ]
```

## <a name="arguments"></a>引数

`@publication= 'publication'`  
トレーサー トークンが挿入されたパブリケーションの名前です。 データ型は**sysname**します。 このパラメーターは必須です。

`[ @tracer_id= ] tracer_id`  
削除するトレーサー トークンの ID です。 データ型は**int**します。既定値は、*null* です。 場合*null*パブリケーションに属するすべてのトレーサー トークンが削除されます。

`[ @cutoff_date= ] cutoff_date`  
この日付が削除されるまでに、パブリケーションに挿入されたトレーサー トークンです。 データ型は**datetime**します。 既定値は、*null* です。

`[ @publisher= ] 'publisher'`  
パブリッシャーの名前です。 データ型は**sysname**します。 既定値は、*null* です。

> [!NOTE]
> このパラメーターは、に対してのみ指定する必要があります以外[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーまたはディストリビューターからストアド プロシージャを実行する場合。

`[ @publisher_db= ] 'publisher_db'`  
パブリケーション データベースの名前です。 データ型は**sysname**します。 既定値は NULL です。 ストアド プロシージャがパブリッシャーで実行される場合、このパラメーターは無視されます。

> [!NOTE]
> ディストリビューターからストアド プロシージャを実行するときに、このパラメーターを指定する必要があります。

## <a name="return-code-values"></a>リターン コードの値

**0** (成功) または**1** (失敗)

## <a name="remarks"></a>コメント

**sp_deletetracertokenhistory**はトランザクション レプリケーションで使用します。  

両方のパラメーターを指定する場合にエラーが発生した*tracer_id*と*cutoff_date*します。

実行されなかった場合**sp_deletetracertokenhistory**トレーサー トークン メタデータを削除するには、定期的にスケジュールされた履歴のクリーンアップが発生した場合、情報は削除されます。

実行することによって、トレーサー トークン Id を決定できます[sp_helptracertokens &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md)またはクエリを実行して、 [MStracer_tokens &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md)システム テーブル。

## <a name="permissions"></a>アクセス許可

以下のスタッフを実行する権限を持つだけ**sp_deletetracertokenhistory**:

- メンバー、 **replmonitor**ディストリビューション データベース内のロール
- メンバー、 **sysadmin**固定サーバー ロール。
- メンバー、 **db_owner**でパブリケーション データベースの固定データベース ロール。
- **Db_owner**の固定データベース。

## <a name="see-also"></a>関連項目

[トランザクション レプリケーションの待機時間の計測および接続の検証](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)

[sp_helptracertokenhistory &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md)
