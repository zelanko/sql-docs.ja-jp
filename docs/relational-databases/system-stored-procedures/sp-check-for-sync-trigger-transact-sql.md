---
title: sp_check_for_sync_trigger (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- filter_TSQL
- sp_check_for_sync_trigger
helpviewer_keywords:
- sp_check_for_sync_trigger
ms.assetid: 54a1e2fd-c40a-43d4-ac64-baed28ae4637
author: stevestein
ms.author: sstein
ms.openlocfilehash: b7d4d26374d7b582f2ba5ddad79dd317145cecd7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070427"
---
# <a name="spcheckforsynctrigger-transact-sql"></a>sp_check_for_sync_trigger (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ユーザー定義トリガーまたはストアド プロシージャが、即時更新サブスクリプションに使われるレプリケーション トリガーのコンテキストで呼び出されているかどうかを判別します。 このストアド プロシージャは、パブリケーション データベースに対して、パブリッシャーまたはサブスクライバーのサブスクリプション データベースで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_check_for_sync_trigger [ @tabid = ] 'tabid'   
    [ , [ @trigger_op = ] 'trigger_output_parameters' OUTPUT ]  
    [ , [ @fonpublisher = ] fonpublisher ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@tabid =** ] '*tabid*'  
 即時更新トリガーに対してチェックされるテーブルのオブジェクト ID です。 *tabid*は**int**既定値はありません。  
  
 [ **@trigger_op =** ] '*trigger_output_parameters*' 出力  
 出力パラメーターが呼び出し元のトリガーの種類を返すかどうかを指定します。 *trigger_output_parameters*は**char (10)** これらの値のいずれかを指定できます。  
  
|[値]|説明|  
|-----------|-----------------|  
|**アドイン**|INSERT トリガーです。|  
|**Upd**|UPDATE トリガーです。|  
|**Del**|DELETE トリガーです。|  
|NULL (既定値)||  
  
`[ @fonpublisher = ] fonpublisher` ストアド プロシージャを実行する場所を指定します。 *fonpublisher*は**ビット**既定値は 0 です。 サブスクライバーで、実行は、0 の場合、および 1 の場合、パブリッシャー側では、実行します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 は、ストアド プロシージャが即時更新トリガーのコンテキスト内で呼び出されていないことを示します。 1 が即時更新トリガーのコンテキスト内で呼び出されるで返されるトリガーの種類は、そのことを示します。  *@trigger_op* します。  
  
## <a name="remarks"></a>コメント  
 **sp_check_for_sync_trigger**スナップショット レプリケーションおよびトランザクション レプリケーションで使用されます。  
  
 **sp_check_for_sync_trigger**レプリケーションとユーザー定義トリガー間を調整するために使用します。 このストアド プロシージャは、レプリケーション トリガーのコンテキスト内で呼び出されているかどうかを判別します。 たとえば、プロシージャを呼び出すことができます**sp_check_for_sync_trigger**ユーザー定義トリガーの本文にします。 場合**sp_check_for_sync_trigger**返します**0**、ユーザー定義トリガーは処理を続行します。 場合**sp_check_for_sync_trigger**返します**1**、ユーザー定義トリガーは終了します。 これにより、ユーザー定義トリガーは、レプリケーション トリガーがテーブルを更新するときに発生しません。  
  
## <a name="example"></a>例  
 次の例では、サブスクライバー テーブルのトリガーで使用できるコードを示します。  
  
```  
DECLARE @retcode int, @trigger_op char(10), @table_id int  
SELECT @table_id = object_id('tablename')  
EXEC @retcode = sp_check_for_sync_trigger @table_id, @trigger_op OUTPUT  
IF @retcode = 1  
RETURN  
```  
  
## <a name="example"></a>例  
 コードは、パブリッシャーの; テーブルのトリガーにも追加できます。コードは似ていますを呼び出して**sp_check_for_sync_trigger**追加のパラメーターが含まれています。  
  
```  
DECLARE @retcode int, @trigger_op char(10), @table_id int, @fonpublisher int  
SELECT @table_id = object_id('tablename')  
SELECT @fonpublisher = 1  
EXEC @retcode = sp_check_for_sync_trigger @table_id, @trigger_op OUTPUT, @fonpublisher  
IF @retcode = 1  
RETURN  
```  
  
## <a name="permissions"></a>アクセス許可  
 **sp_check_for_sync_trigger**で SELECT 権限を持つ任意のユーザーがストアド プロシージャを実行することができます、 [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)システム ビュー。  
  
## <a name="see-also"></a>関連項目  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
