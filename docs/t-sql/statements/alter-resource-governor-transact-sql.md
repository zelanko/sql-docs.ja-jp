---
title: "リソース ガバナーの変更 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER RESOURCE GOVERNOR
- ALTER_RESOURCE_GOVERNOR_TSQL
- ALTER RESOURCE GOVERNOR RECONFIGURE
- ALTER_RESOURCE_GOVERNOR_RECONFIGURE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER RESOURCE GOVERNOR
- RECONFIGURE, ALTER RESOURCE GOVERNOR
ms.assetid: 442c54bf-a0a6-4108-ad20-db910ffa6e3c
caps.latest.revision: 49
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ac7ae791ec7867b13a8547ec60436f25536cd5b7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-resource-governor-transact-sql"></a>ALTER RESOURCE GOVERNOR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このステートメントを使用では、次のリソース ガバナー操作を実行して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   ときに指定した構成の変更の適用の作成 |ALTER |DROP WORKLOAD GROUP または CREATE |ALTER |DROP RESOURCE POOL または CREATE |ALTER |DROP EXTERNAL RESOURCE POOL ステートメントが発行されます。  
  
-   リソース ガバナーの有効化と無効化  
  
-   受信要求の分類の構成  
  
-   ワークロード グループ統計とリソース プール統計のリセット  
  
-   ディスク ボリュームごとの最大 I/O 操作数の設定  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
ALTER RESOURCE GOVERNOR   
      { DISABLE | RECONFIGURE }  
    | WITH ( CLASSIFIER_FUNCTION = { schema_name.function_name | NULL } )  
    | RESET STATISTICS  
    | WITH ( MAX_OUTSTANDING_IO_PER_VOLUME = value )   
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 DISABLE  
 リソース ガバナーを無効にします。 リソース ガバナーを無効にすると、結果は次のようになります。  
  
-   分類関数は実行されません。  
  
-   すべての新しい接続が、既定のグループに自動的に分類されます。  
  
-   システムによって開始される要求は、内部ワークロード グループに分類されます。  
  
-   ワークロード グループとリソース プールの既存の設定は、すべて既定値にリセットされます。 この場合、制限に達してもイベントは発生しません。  
  
-   通常のシステム監視は影響を受けません。  
  
-   構成は変更できますが、リソース ガバナーを有効にするまで変更は反映されません。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の再起動時に、リソース ガバナーはその構成を読み込みません。このとき、既定および内部のグループとプールのみが存在します。  
  
 RECONFIGURE  
 リソース ガバナーが有効でない場合、RECONFIGURE でリソース ガバナーを有効にします。 リソース ガバナーを有効にするには、次の結果があります。  
  
-   新しい接続に対して分類関数が実行され、それらのワークロードがワークロード グループに割り当てられます。  
  
-   リソース ガバナー構成で指定されているリソース制限が有効になり適用されます。  
  
-   リソース ガバナーを有効にする前に存在していた要求は、リソース ガバナーが無効になっているときに行われた構成の変更の影響を受けます。  
  
 RECONFIGURE が任意の構成を適用してリソース ガバナーが実行されているときに変更が要求されたときに、CREATE |ALTER |DROP WORKLOAD GROUP または CREATE |ALTER |DROP RESOURCE POOL または CREATE |ALTER |DROP EXTERNAL RESOURCE POOL ステートメントが実行されます。  
  
> [!IMPORTANT]  
>  構成の変更を有効にするには、ALTER RESOURCE GOVERNOR RECONFIGURE を実行する必要があります。  
  
 CLASSIFIER_FUNCTION = { *schema_name***.***function_name* |NULL}  
 指定された分類関数を登録*schema_name.function_name*です。 この関数によってすべての新しいセッションが分類され、セッションの要求とクエリがワークロード グループに割り当てられます。 NULL を使用すると、新しいセッションは既定のワークロード グループに自動的に割り当てられます。  
  
 RESET STATISTICS  
 すべてのワークロード グループとリソース プールの統計をリセットします。 詳細については、次を参照してください。 [sys.dm_resource_governor_workload_groups & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md)と[sys.dm_resource_governor_resource_pools & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md).  
  
 MAX_OUTSTANDING_IO_PER_VOLUME =*値*  
 **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 キューに登録される I/O 操作のディスク ボリュームごとの最大数を設定します。 これらの I/O 操作では、任意のサイズの読み取りや書き込みを行うことができます。  MAX_OUTSTANDING_IO_PER_VOLUME の最大値は 100 です。 これはパーセントではありません。 この設定の目的は、ディスク ボリュームの IO 特性に合わせて IO リソース管理をチューニングすることです。 さまざまな値をテストし、IOMeter などの調整ツールの使用を検討することをお勧め[DiskSpd](https://gallery.technet.microsoft.com/DiskSpd-a-robust-storage-6cd2f223)、や SQLIO、記憶域サブシステムの最大値を識別する (非推奨)。 この設定では、システム レベルの安全性チェックが提供され、他のプールで MAX_IOPS_PER_VOLUME が無制限に設定されている場合でも、SQL Server でリソース プールの最小 IOPS を満たすことができます。 MAX_IOPS_PER_VOLUME の詳細については、次を参照してください。 [CREATE RESOURCE POOL](../../t-sql/statements/create-resource-pool-transact-sql.md)です。  
  
## <a name="remarks"></a>解説  
 ALTER RESOURCE GOVERNOR DISABLE、ALTER RESOURCE GOVERNOR RECONFIGURE、および ALTER RESOURCE GOVERNOR RESET STATISTICS は、ユーザー トランザクション内で使用できません。  
  
 RECONFIGURE パラメーターは、リソース ガバナー構文の一部でありと混同しないで[再構成](../../t-sql/language-elements/reconfigure-transact-sql.md)、個別の DDL ステートメントであります。  
  
 DDL ステートメントを実行する前に、リソース ガバナーの状態について詳しく理解しておくことをお勧めします。 詳細については、次を参照してください。[リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)です。  
  
## <a name="permissions"></a>Permissions  
 CONTROL SERVER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-starting-the-resource-governor"></a>A. リソース ガバナーを起動する  
 ときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が最初にインストールされているリソース ガバナーが無効になっています。 リソース ガバナーを起動する例を次に示します。 このステートメントを実行するとリソース ガバナーが実行され、定義済みのワークロード グループおよびリソース プールを使用できるようになります。  
  
```  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
```  
  
### <a name="b-assigning-new-sessions-to-the-default-group"></a>B. 新しいセッションを既定のグループに割り当てる  
 次の例では、リソース ガバナー構成から既存の分類関数を削除することによって、すべての新しいセッションを既定のワークロード グループに割り当てます。 関数が分類関数として指定されていない場合、新しいセッションはすべて既定のワークロード グループに割り当てられます。 この変更は新しいセッションにのみ適用されます。 既存のセッションは影響を受けません。  
  
```  
ALTER RESOURCE GOVERNOR WITH (CLASSIFIER_FUNCTION = NULL);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
```  
  
### <a name="c-creating-and-registering-a-classifier-function"></a>C. 分類関数を作成して登録する  
 次の例は、という名前の分類子関数を作成`dbo.rgclassifier_v1`です。 この関数によって、ユーザー名またはアプリケーション名に基づいてすべての新しいセッションが分類され、セッションの要求とクエリが、指定されたワークロード グループに割り当てられます。 指定されたユーザー名またはアプリケーション名にマップされていないセッションは、既定のワークロード グループに割り当てられます。 次に分類関数が登録され、構成の変更が適用されます。  
  
```  
-- Store the classifier function in the master database.  
USE master;  
GO  
SET ANSI_NULLS ON;  
GO  
SET QUOTED_IDENTIFIER ON;  
GO  
CREATE FUNCTION dbo.rgclassifier_v1() RETURNS sysname   
WITH SCHEMABINDING  
AS  
BEGIN  
-- Declare the variable to hold the value returned in sysname.  
    DECLARE @grp_name AS sysname  
-- If the user login is 'sa', map the connection to the groupAdmin  
-- workload group.   
    IF (SUSER_NAME() = 'sa')  
        SET @grp_name = 'groupAdmin'  
-- Use application information to map the connection to the groupAdhoc  
-- workload group.  
    ELSE IF (APP_NAME() LIKE '%MANAGEMENT STUDIO%')  
        OR (APP_NAME() LIKE '%QUERY ANALYZER%')  
            SET @grp_name = 'groupAdhoc'  
-- If the application is for reporting, map the connection to  
-- the groupReports workload group.  
    ELSE IF (APP_NAME() LIKE '%REPORT SERVER%')  
        SET @grp_name = 'groupReports'  
-- If the connection does not map to any of the previous groups,  
-- put the connection into the default workload group.  
    ELSE  
        SET @grp_name = 'default'  
    RETURN @grp_name  
END;  
GO  
-- Register the classifier user-defined function and update the   
-- the in-memory configuration.  
ALTER RESOURCE GOVERNOR WITH (CLASSIFIER_FUNCTION=dbo.rgclassifier_v1);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
### <a name="d-resetting-statistics"></a>D. 統計をリセットする  
 次の例では、すべてのワークロード グループとリソース プールの統計をリセットします。  
  
```  
ALTER RESOURCE GOVERNOR RESET STATISTICS;  
```  
  
### <a name="e-setting-the-maxoutstandingiopervolume-option"></a>E. MAX_OUTSTANDING_IO_PER_VOLUME オプションを設定する  
 次の例では、MAX_OUTSTANDING_IO_PER_VOLUME オプションが 20 に設定されます。  
  
```  
ALTER RESOURCE GOVERNOR  
WITH (MAX_OUTSTANDING_IO_PER_VOLUME = 20);   
```  
  
## <a name="see-also"></a>参照  
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)   
 [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)   
 [DROP EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-external-resource-pool-transact-sql.md)   
 [外部リソース プールの変更 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-workload-group-transact-sql.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [[リソース ガバナー]](../../relational-databases/resource-governor/resource-governor.md)   
 [sys.dm_resource_governor_workload_groups & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md)   
 [sys.dm_resource_governor_resource_pools & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)  
  
  

