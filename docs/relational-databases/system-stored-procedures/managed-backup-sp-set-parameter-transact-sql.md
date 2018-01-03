---
title: "managed_backup.sp_set_parameter (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
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
- sp_set_parameter_TSQL
- sp_set_parameter
- smart_admin.sp_set_parameter
- smart_admin.sp_set_parameter_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sp_set_parameter
- smart_admin.sp_set_parameter
ms.assetid: bd8ae5fd-1337-4b7f-b0a4-153cbca9fa5f
caps.latest.revision: "15"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 31460ed7e3e972d87d9c6461ad78d5560fd67861
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2018
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
 値を設定するパラメーターの名前。 @parameter_namenvarchar (128)。 使用可能なパラメーター名は**SSMBackup2WANotificationEmailIds**、 **SSMBackup2WADebugXevent**、 **SSMBackup2WAEnableUserDefinedPolicy**、 **FileRetentionDebugXevent**、および**StorageOperationDebugXevent**です。  
  
 @parameter_value  
 パラメーターに設定する値。 @parameter値は、nvarchar (128) です。  許容されているパラメーターの名前と値のペアは次のとおりです。  
  
-   @parameter_name= 'SSMBackup2WANotificationEmailIds': @parameter_value = '電子メール'  
  
-   @parameter_name= 'SSMBackup2WAEnableUserDefinedPolicy': @parameter_value = {'true' |false'}  
  
-   @parameter_name= 'SSMBackup2WADebugXevent': @parameter_value = {'true' |false'}  
  
-   @parameter_name= 'FileRetentionDebugXevent': @parameter_value = {'true' |false'}  
  
-   @parameter_name'StorageOperationDebugXevent' = = {'true' |false'}  
  
## <a name="return-code-value"></a>リターン コード値  
 0 (成功) または 1 (失敗)  
  
## <a name="best-practices"></a>ベスト プラクティス  
 ステートメントまたはルーチンの実行時にユーザーが知っておく必要があるベスト プラクティスを説明するセクション (省略可) です。  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>アクセス許可  
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
  
  
