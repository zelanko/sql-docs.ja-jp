---
title: sp_resetsnapshotdeliveryprogress (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_resetsnapshotdeliveryprogress
- sp_resetsnapshotdeliveryprogress_TSQL
helpviewer_keywords:
- sp_resetsnapshotdeliveryprogress
ms.assetid: 5df7d86b-d343-4d9b-88b1-74429ed092e6
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 899a590bb2c634568399aca6f5520b52d26a52b4
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43022738"
---
# <a name="spresetsnapshotdeliveryprogress-transact-sql"></a>sp_resetsnapshotdeliveryprogress (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  スナップショットの配信が再起動できるように、プル サブスクリプションのスナップショット配信処理をリセットします。 サブスクライバー側でサブスクリプション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_resetsnapshotdeliveryprogress [ [ @verbose_level = ] verbose_level ]  
    [ , [ @drop_table = ] 'drop_table' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@verbose_level**=] *verbose_level*  
 返される情報の量を指定します。 *verbose_level*は**int**、既定値は**1**します。 値**1**で必要なロックを取得できないかどうかにエラーがあることを意味が返される、 **MSsnapshotdeliveryprogress**テーブル、および**0**エラーが返されないことを意味します。  
  
 [ **@drop_table**=] **'***drop_table***'**  
 削除するか、スナップショットのテーブルを含むの進行状況の情報を切り捨てるかどうかです。*drop_table*は**nvarchar (5)**、既定値は**FALSE**します。 FALSE は、テーブルが切り捨てられることを意味します。TRUE は、テーブルが削除されることを意味します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_resetsnapshotdeliveryprogress**のすべての行を削除、 **MSsnapshotdeliveryprogress**テーブル。 これは実質的に、スナップショット配信処理で以前に実行されたすべての処理によってサブスクリプション データベースに残されたメタデータをすべて削除することになります。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_resetsnapshotdeliveryprogress**します。  
  
## <a name="see-also"></a>参照  
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
