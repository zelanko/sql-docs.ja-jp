---
title: sp_check_for_sync_trigger (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- filter_TSQL
- sp_check_for_sync_trigger
helpviewer_keywords:
- sp_check_for_sync_trigger
ms.assetid: 54a1e2fd-c40a-43d4-ac64-baed28ae4637
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: a77f5bfd92ca2af52e6d8949a98e4aa24c908534
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spcheckforsynctrigger-transact-sql"></a>sp_check_for_sync_trigger (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ユーザー定義トリガーまたはストアド プロシージャが、即時更新サブスクリプションに使われるレプリケーション トリガーのコンテキストで呼び出されているかどうかを判別します。 このストアド プロシージャは、パブリッシャー側のパブリケーション データベースまたはサブスクライバーのサブスクリプション データベースで実行されます。  
  
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
  
|値|Description|  
|-----------|-----------------|  
|**アドイン**|INSERT トリガーです。|  
|**Upd**|UPDATE トリガーです。|  
|**Del**|DELETE トリガーです。|  
|NULL (既定値)||  
  
 [  **@fonpublisher =** ] *fonpublisher*  
 ストアド プロシージャの実行場所を指定します。 *fonpublisher*は**ビット**既定値は 0 です。 0 の場合はサブスクライバー側、1 の場合はパブリッシャー側で実行します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 の場合、ストアド プロシージャが即時更新トリガーのコンテキスト内で呼び出されていないことを示します。 1 はことを示しますが、即時更新トリガーのコンテキスト内で呼び出されるに返されるトリガーの種類 *@trigger_op*です。  
  
## <a name="remarks"></a>解説  
 **sp_check_for_sync_trigger**はスナップショット レプリケーションおよびトランザクション レプリケーションで使用します。  
  
 **sp_check_for_sync_trigger**レプリケーションおよびユーザー定義トリガー間を調整するために使用します。 このストアド プロシージャは、レプリケーション トリガーのコンテキスト内で呼び出されているかどうかを判別します。 たとえば、プロシージャを呼び出すことができます**sp_check_for_sync_trigger**ユーザー定義のトリガーの本文にします。 場合**sp_check_for_sync_trigger**返します**0**、ユーザー定義トリガーは処理を続行します。 場合**sp_check_for_sync_trigger**返します**1**、ユーザー定義トリガーは終了します。 ユーザー定義トリガーは、レプリケーション トリガーがテーブルを更新するときには起動されません。  
  
## <a name="example"></a>例  
 次の例は、サブスクライバー テーブルのトリガーで使用できるコードを示しています。  
  
```  
DECLARE @retcode int, @trigger_op char(10), @table_id int  
SELECT @table_id = object_id('tablename')  
EXEC @retcode = sp_check_for_sync_trigger @table_id, @trigger_op OUTPUT  
IF @retcode = 1  
RETURN  
```  
  
## <a name="example"></a>例  
 コードは、パブリッシャーの; テーブルのトリガーにも追加できます。コードと同様への呼び出しが、 **sp_check_for_sync_trigger**追加のパラメーターが含まれています。  
  
```  
DECLARE @retcode int, @trigger_op char(10), @table_id int, @fonpublisher int  
SELECT @table_id = object_id('tablename')  
SELECT @fonpublisher = 1  
EXEC @retcode = sp_check_for_sync_trigger @table_id, @trigger_op OUTPUT, @fonpublisher  
IF @retcode = 1  
RETURN  
```  
  
## <a name="permissions"></a>権限  
 **sp_check_for_sync_trigger**で SELECT 権限を持つユーザーがストアド プロシージャを実行することができます、 [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)システム ビューです。  
  
## <a name="see-also"></a>参照  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
