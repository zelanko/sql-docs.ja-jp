---
title: managed_backup.sp_set_parameter (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_set_parameter_TSQL
- sp_set_parameter
- smart_admin.sp_set_parameter
- smart_admin.sp_set_parameter_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_set_parameter
- smart_admin.sp_set_parameter
ms.assetid: bd8ae5fd-1337-4b7f-b0a4-153cbca9fa5f
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2a9f1d5eeec1fc5b24fbc1974d27e9f4b5efd00d
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="managedbackupspsetparameter-transact-sql"></a>managed_backup.sp_set_parameter (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  指定された Smart Admin システム パラメーターの値を設定します。  
  
 使用可能なパラメーターは、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]に関連します。 これらのパラメーターは、電子メール通知の設定、特定の拡張イベントの有効化、およびユーザーが設定したポリシー ベースの管理ポリシーの有効化に使用されます。 パラメーター名とパラメーター値のペアを指定する必要があります。  

  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
EXEC managed_backup.sp_set_parameter   
    [@parameter_name = ] {'SSMBackup2WANotificationEmailIds' | 'SSMBackup2WAEnableUserDefinedPolicy' | 'SSMBackup2WADebugXevent' | 'FileRetentionDebugXevent' | 'StorageOperationDebugXevent'}  
    ,[@parameter_value = ] 'parameter_value'  
```  
  
##  <a name="Arguments"></a> 引数  
 @parameter_name  
 値を設定するパラメーターの名前。 @parameter_name nvarchar (128)。 使用可能なパラメーター名は**SSMBackup2WANotificationEmailIds**、 **SSMBackup2WADebugXevent**、 **SSMBackup2WAEnableUserDefinedPolicy**、 **FileRetentionDebugXevent**、および**StorageOperationDebugXevent**です。  
  
 @parameter_value  
 パラメーターに設定する値。 @parameter 値は、nvarchar (128) です。  許容されているパラメーターの名前と値のペアは次のとおりです。  
  
-   @parameter_name = 'SSMBackup2WANotificationEmailIds': @parameter_value = '電子メール'  
  
-   @parameter_name = 'SSMBackup2WAEnableUserDefinedPolicy': @parameter_value = {'true' |false'}  
  
-   @parameter_name = 'SSMBackup2WADebugXevent': @parameter_value = {'true' |false'}  
  
-   @parameter_name = 'FileRetentionDebugXevent' : @parameter_value  = { 'true' | 'false' }  
  
-   @parameter_name = 'StorageOperationDebugXevent' = { 'true' | 'false' }  
  
## <a name="return-code-value"></a>リターン コード値  
 0 (成功) または 1 (失敗)  
  
## <a name="best-practices"></a>ベスト プラクティス  
 ステートメントまたはルーチンの実行時にユーザーが知っておく必要があるベスト プラクティスを説明するセクション (省略可) です。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>権限  
 必要があります**EXECUTE**に対するアクセス許可**managed_backup.sp_set_parameter**ストアド プロシージャです。  
  
## <a name="examples"></a>使用例  
 次の例では、運用およびデバッグの拡張イベントを有効にします。  
  
```  
-- to enable operational events  
Use msdb;  
Go  
         EXEC managed_backup.sp_set_parameter 'FileRetentionOperationalXevent', 'True'  
--  to enable debug events  
Use msdb;  
Go  
         EXEC managed_backup.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
```  
  
 次の例では、エラーと警告の電子メール通知を有効にし、通知の送信先に使用する emailID を設定します。  
  
```  
Use msdb  
Go  
EXEC managed_backup.sp_set_parameter @parameter_name = 'SSMBackup2WANotificationEmailIds', @parameter_value = '<email address>'  
  
```  
  
  
