---
title: sp_check_for_sync_trigger (Transact-sql) |Microsoft Docs
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6fd7af5a486928e0dca9f5b2281e0b53c5038e74
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85771333"
---
# <a name="sp_check_for_sync_trigger-transact-sql"></a>sp_check_for_sync_trigger (Transact-sql)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  ユーザー定義トリガーまたはストアド プロシージャが、即時更新サブスクリプションに使われるレプリケーション トリガーのコンテキストで呼び出されているかどうかを判別します。 このストアドプロシージャは、パブリッシャー側でパブリケーションデータベースに対して実行されるか、サブスクライバー側でサブスクリプションデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_check_for_sync_trigger [ @tabid = ] 'tabid'   
    [ , [ @trigger_op = ] 'trigger_output_parameters' OUTPUT ]  
    [ , [ @fonpublisher = ] fonpublisher ]  
```  
  
## <a name="arguments"></a>引数  
 [** @tabid =** ] '*tabid*'  
 即時更新トリガーに対してチェックされるテーブルのオブジェクト ID です。 *tabid*は**int**で、既定値はありません。  
  
 [** @trigger_op =** ] '*trigger_output_parameters*' 出力  
 出力パラメーターが呼び出し元のトリガーの種類を返すかどうかを指定します。 *trigger_output_parameters*は**char (10)** で、次のいずれかの値を指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**アドイン**|INSERT トリガーです。|  
|**Upd**|UPDATE トリガーです。|  
|**Delete**|DELETE トリガーです。|  
|NULL (既定値)||  
  
`[ @fonpublisher = ] fonpublisher`ストアドプロシージャが実行される場所を指定します。 この**場合、既定***値は 0*です。 0の場合、サブスクライバーで実行されます。1の場合、パブリッシャーで実行されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0は、ストアドプロシージャが即時更新トリガーのコンテキスト内で呼び出されていないことを示します。 1は、即時更新トリガーのコンテキスト内で呼び出されており、 * \@ trigger_op*で返されるトリガーの種類であることを示します。  
  
## <a name="remarks"></a>Remarks  
 **sp_check_for_sync_trigger**は、スナップショットレプリケーションおよびトランザクションレプリケーションで使用します。  
  
 **sp_check_for_sync_trigger**は、レプリケーションとユーザー定義トリガーを調整するために使用されます。 このストアド プロシージャは、レプリケーション トリガーのコンテキスト内で呼び出されているかどうかを判別します。 たとえば、ユーザー定義トリガーの本文でプロシージャ**sp_check_for_sync_trigger**を呼び出すことができます。 **Sp_check_for_sync_trigger**が**0**を返した場合、ユーザー定義トリガーは処理を続行します。 **Sp_check_for_sync_trigger**が**1**を返した場合、ユーザー定義のトリガーは終了します。 これにより、レプリケーショントリガーによってテーブルが更新されたときに、ユーザー定義のトリガーが起動しなくなります。  
  
## <a name="example"></a>例  
 次の例は、サブスクライバーテーブルのトリガーで使用できるコードを示しています。  
  
```  
DECLARE @retcode int, @trigger_op char(10), @table_id int  
SELECT @table_id = object_id('tablename')  
EXEC @retcode = sp_check_for_sync_trigger @table_id, @trigger_op OUTPUT  
IF @retcode = 1  
RETURN  
```  
  
## <a name="example"></a>例  
 このコードは、パブリッシャーのテーブルのトリガーに追加することもできます。コードも似ていますが、 **sp_check_for_sync_trigger**の呼び出しには追加のパラメーターが含まれています。  
  
```  
DECLARE @retcode int, @trigger_op char(10), @table_id int, @fonpublisher int  
SELECT @table_id = object_id('tablename')  
SELECT @fonpublisher = 1  
EXEC @retcode = sp_check_for_sync_trigger @table_id, @trigger_op OUTPUT, @fonpublisher  
IF @retcode = 1  
RETURN  
```  
  
## <a name="permissions"></a>アクセス許可  
 **sp_check_for_sync_trigger**ストアドプロシージャは、 [sys. objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)システムビューで SELECT 権限を持つ任意のユーザーが実行できます。  
  
## <a name="see-also"></a>関連項目  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
