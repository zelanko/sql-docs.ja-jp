---
title: managed_backup。 sp_set_parameter (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 838a8b0d998476a37b0dd4d30cab5041ad4276a0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67942032"
---
# <a name="managed_backupsp_set_parameter-transact-sql"></a>managed_backup。 sp_set_parameter (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  指定した Smart Admin システムパラメーターの値を設定します。  
  
 使用可能なパラメーターは、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]に関連します。 これらのパラメーターは、電子メール通知の設定、特定の拡張イベントの有効化、およびユーザー設定ポリシーベースの管理ポリシーの有効化に使用されます。 パラメーター名とパラメーター値のペアを指定する必要があります。  

  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
EXEC managed_backup.sp_set_parameter   
    [@parameter_name = ] {'SSMBackup2WANotificationEmailIds' | 'SSMBackup2WAEnableUserDefinedPolicy' | 'SSMBackup2WADebugXevent' | 'FileRetentionDebugXevent' | 'StorageOperationDebugXevent'}  
    ,[@parameter_value = ] 'parameter_value'  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>数値  
 @parameter_name  
 値を設定するパラメーターの名前。 @parameter_nameNVARCHAR (128) です。 使用できるパラメーター名は、 **SSMBackup2WANotificationEmailIds**、 **SSMBackup2WADebugXevent**、 **SSMBackup2WAEnableUserDefinedPolicy**、 **FileRetentionDebugXevent**、および**storageoperationdebugxevent**です。  
  
 @parameter_value  
 設定するパラメーターの値。 @parameter値は NVARCHAR (128) です。  許容されているパラメーターの名前と値のペアは次のとおりです。  
  
-   @parameter_name= ' SSMBackup2WANotificationEmailIds ': @parameter_value = ' email '  
  
-   @parameter_name= ' SSMBackup2WAEnableUserDefinedPolicy ': @parameter_value = {' true ' |' false '}  
  
-   @parameter_name= ' SSMBackup2WADebugXevent ': @parameter_value = {' true ' |' false '}  
  
-   @parameter_name= ' FileRetentionDebugXevent ': @parameter_value = {' true ' |' false '}  
  
-   @parameter_name= ' StorageOperationDebugXevent ' = {' true ' |' false '}  
  
## <a name="return-code-value"></a>リターン コード値  
 0 (成功) または 1 (失敗)  
  
## <a name="best-practices"></a>推奨する運用方法  
 ステートメントまたはルーチンの実行時にユーザーが知る必要のあるベストプラクティスについて説明する省略可能なセクションです。  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>アクセス許可  
 Managed_backup に対する**EXECUTE**権限が必要です **。 sp_set_parameter**ストアドプロシージャ。  
  
## <a name="examples"></a>使用例  
 次の例では、拡張イベントの操作とデバッグを有効にします。  
  
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
  
 次の例では、エラーと警告の電子メール通知を有効にし、通知をに送信するために使用する emailID を設定します。  
  
```  
Use msdb  
Go  
EXEC managed_backup.sp_set_parameter @parameter_name = 'SSMBackup2WANotificationEmailIds', @parameter_value = '<email address>'  
  
```  
  
  
