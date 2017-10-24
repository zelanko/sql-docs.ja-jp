---
title: "外部リソース プール (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE EXTERNAL RESOURCE POOL
- CREATE EXTERNAL_RESOURCE_POOL_TSQL
- EXTERNAL RESOURCE POOL
- EXTERNAL_RESOURCE_POOL_TSQL
- EXTERNAL RESOURCE
- EXTERNAL_RESOURCE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE EXTERNAL RESOURCE POOL statement
ms.assetid: 8cc798ad-c395-461c-b7ff-8c561c098808
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 32c33076f26332f2a8510c4660696106bef824b5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-external-resource-pool-transact-sql"></a>外部リソース プール (TRANSACT-SQL) を作成します。
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  外部プロセス用のリソースを定義するために使用する外部プールを作成します。 R Services 外部プールは`rterm.exe`、 `BxlServer.exe`、およびそれらにより生成された他のプロセスです。 リソース プールでは、データベース エンジンのインスタンスの物理リソース (メモリや Cpu) のサブセットを表します。 データベース管理者は、リソース ガバナーを使用することで、サーバー リソースを最大 64 個までのリソース プールに分散できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [TRANSACT-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
CREATE EXTERNAL RESOURCE POOL pool_name  
[ WITH (  
    [ MAX_CPU_PERCENT = value ]  
    [ [ , ] AFFINITY CPU =    
            {  
                AUTO   
              | ( <cpu_range_spec> )   
              | NUMANODE = ( <NUMA_node_id> )   
            } ]   
    [ [ , ] MAX_MEMORY_PERCENT = value ]  
    [ [ , ] MAX_PROCESSES = value ]   
    )   
]  
[ ; ]  
  
<CPU_range_spec> ::=    
{ CPU_ID | CPU_ID  TO CPU_ID } [ ,...n ]  
```  
  
## <a name="arguments"></a>引数  
 *pool_name*  
 外部リソース プールのユーザー定義名です。 *pool_name*は、英数字、最大 128 文字を使用できますがのインスタンス内で一意である必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、規則に従う必要がありますと[識別子](../../relational-databases/databases/database-identifiers.md)です。  
  
 MAX_CPU_PERCENT =*値*  
 最大平均 CPU 帯域幅 CPU の競合がある場合、外部リソース プールのすべての要求を受信するを指定します。 *値*で、既定の設定 100 の整数です。 許容範囲*値*は 1 ~ 100 です。  
  
 アフィニティ {CPU = 自動 |( \<CPU_range_spec >) |NUMANODE = (\<NUMA_node_range_spec >)} 外部リソース プールを特定の Cpu にアタッチします。 既定値は AUTO です。  
  
 アフィニティ CPU = **(** \<CPU_range_spec > **)**外部リソース プールをマップする、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]特定 CPU_IDs で識別される Cpu。 
  
 AFFINITY NUMANODE を使用すると = **(** \<NUMA_node_range_spec > **)**、外部リソース プールが関連付けられ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]指定した NUMA に対応する物理 Cpuノードまたはノードの範囲です。 
  
 MAX_MEMORY_PERCENT =*値*  
 この外部リソース プールの要求で使用できる合計サーバー メモリを指定します。 *値*で、既定の設定 100 の整数です。 許容範囲*値*は 1 ~ 100 です。  
  
 MAX_PROCESSES =*値*  
 外部リソース プールのプロセスの最大数を指定します。 バインドは、プールは、必ずコンピューター リソースの無制限のしきい値を設定する場合は 0 を指定します。 既定値は 0 です。  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]を実行すると、リソース プールを実装して、 [ALTER RESOURCE GOVERNOR RECONFIGURE](../../t-sql/statements/alter-resource-governor-transact-sql.md)ステートメントです。  
  
 リソース プールの詳細については、次を参照してください。[リソース ガバナー リソース プール](../../relational-databases/resource-governor/resource-governor-resource-pool.md)、 [sys.resource_governor_external_resource_pools & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)、および[sys.dm_resource_governor_external_resource_pool_affinity & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 必要があります`CONTROL SERVER`権限です。  
  
## <a name="examples"></a>使用例  
 次のステートメントでは、CPU 使用率を 75 パーセントであり、コンピューターで使用可能なメモリの 30% の最大メモリ量に制限する外部プールを定義します。  
  
```  
CREATE EXTERNAL RESOURCE POOL ep_1  
WITH (  
    MAX_CPU_PERCENT = 75  
    , AFFINITY CPU = AUTO  
    , MAX_MEMORY_PERCENT = 30  
);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [external scripts enabled サーバー構成オプション](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
 [sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)   
 [SQL Server R サービス](../../advanced-analytics/r-services/sql-server-r-services.md)   
 [SQL Server R Services の既知の問題](../../advanced-analytics/r-services/known-issues-for-sql-server-r-services.md)   
 [外部リソース プールの変更 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)   
 [DROP EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-external-resource-pool-transact-sql.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [リソース ガバナー リソース プール](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)   
 [sys.dm_resource_governor_external_resource_pool_affinity & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  


