---
title: "方法: R 用のリソース プールを作成する | Microsoft Docs"
ms.custom: 
ms.date: 10/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7f7f6e4-774d-4b45-b94a-f06c51718475
caps.latest.revision: 19
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: be3afb3a1ff5175fbb3d0735cde59bd19bb47f6c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="how-to-create-a-resource-pool-for-r"></a>方法: R 用のリソース プールを作成する
  このトピックでは、特に R のワークロードを管理するためのリソース プールを [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] で作成する方法について説明します。 R Services (In-Database) はインストール済みであり、R で使用されるリソースのより細かい管理をサポートするために [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インスタンスを再構成することを前提とします。  
  
 サーバー リソースの管理の詳細については、「[Resource Governor (リソース ガバナー)](../../relational-databases/resource-governor/resource-governor.md)」と「[Resource Governor Related Dynamic Management Views &#40;Transact-SQL&#41; (リソース ガバナーに関連する動的管理ビュー (SQL))](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)」を参照してください。  
  
 **手順**  
  
1.  既存のリソース プールの状態を確認する  
  
2.  サーバー リソース プールを変更する  
  
3.  外部プロセス用の新しいリソース プールを作成する  
  
4.  R 要求を識別する分類子関数を作成する  
  
5.  新しい外部リソース プールが R ジョブをキャプチャすることを確認する  
  
##  <a name="bkmk_ReviewStatus"></a>既存のリソース プールの状態を確認する  
  
1.  最初に、サーバーの既定のプールに割り当てられているリソースを確認します。  
  
    ```  
    SELECT * FROM sys.resource_governor_resource_pools WHERE name = 'default'  
    ```  
     **結果**

    |pool_id|name|min_cpu_percent|max_cpu_percent|min_memory_percent|max_memory_percent|cap_cpu_percent|min_iops_per_volume|max_iops_per_volume|  
    |-|-|-|-|-|-|-|-|-|  
    |2|既定値 (default)|0|100|0|100|100|0|0|  

2.  既定の**外部**リソース プールに割り当てられているリソースを確認します。  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pools WHERE name = 'default'  
    ```  
     
    **結果**

    |external_pool_id|name|max_cpu_percent|max_memory_percent|max_processes|version|  
    |-|-|-|-|-|-|  
    |2|既定値 (default)|100|20|0|2|  
 
3.  これらのサーバーの既定の設定では、R ランタイムが大半のタスクを完了するにはリソース不足になる可能性があります。 これを変更するには、サーバーのリソース使用率を次のように変更する必要があります。  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が使用できるコンピューターの最大メモリを減らす  
  
    -   外部プロセスが使用できるコンピューターの最大メモリを増やす  
  
## <a name="modify-server-resource-usage"></a>サーバーのリソース使用率を変更する  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] で、次のステートメントを実行して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のメモリ使用量を [最大サーバー メモリ] の値の **60%** に制限します。  
  
    ```  
    ALTER RESOURCE POOL "default" WITH (max_memory_percent = 60);  
    ```  
  
2.  同様に、次のステートメントを実行して、外部プロセスによるメモリの使用量をコンピューター リソース全体の **40%** に制限します。  
  
    ```  
    ALTER EXTERNAL RESOURCE POOL "default" WITH (max_memory_percent = 40);  
    ```  
  
3.  これらの変更を適用するには、リソース ガバナーを次のように再構成して再起動する必要があります。  
  
    ```  
    ALTER RESOURCE GOVERNOR reconfigure;  
    ```  
  
    > [!NOTE]  
    >  これらは、単に手始めとして推奨する設定です。R の要件と他のサーバー プロセスを評価して、環境とワークロードに適したバランスを判断する必要があります。  
  
## <a name="create-a-user-defined-external-resource-pool"></a>ユーザー定義の外部リソース プールを作成する  
  
1.  リソース ガバナーの構成に対する変更はサーバー全体に適用され、サーバーの既定のプールを使用するワークロードだけではなく、外部プールを使用するワークロードにも影響します。  
  
     そのため、優先するワークロードを細かく制御するために、新しいユーザー定義の外部リソース プールを作成できます。 さらに、分類子関数を定義して、外部リソース プールに割り当てる必要があります。  
  
     新しい "*ユーザー定義の外部リソース プール*" の作成から始めます。 次の例では、プールに **ds_ep** という名前を付けています。  
  
    ```  
    CREATE EXTERNAL RESOURCE POOL ds_ep WITH (max_memory_percent = 40);  
    ```  
  
     新しい **EXTERNAL** キーワードが使用されていることに注意してください。  
  
2.  セッション要求の管理で使用する `ds_wg` という名前のワークロード グループを作成します。 SQL クエリでは既定のプールを使用し、すべての外部プロセスのクエリでは `ds_ep` プールを使用します。  
  
    ```  
    CREATE WORKLOAD GROUP ds_wg WITH (importance = medium) USING "default", EXTERNAL "ds_ep";  
    ```  
  
     要求は、要求を分類することができない場合、またはその他の分類エラーが発生した場合は、既定のグループに割り当てられます。  
  
     詳細については、「[Resource Governor Workload Group (リソース ガバナー ワークロード グループ)](../../relational-databases/resource-governor/resource-governor-workload-group.md)」と「[CREATE WORKLOAD GROUP &#40;Transact-SQL&#41; (ワークロード グループの作成 (TRANSACT-SQL))](../../t-sql/statements/create-workload-group-transact-sql.md)」を参照してください。  
  
## <a name="create-a-classification-function-for-r"></a>R 用の分類子関数を作成する  
  
1.  分類子関数は、受信タスクを検査して、タスクが現在のリソース プールを使用して実行できるかどうかを決定します。 分類子関数の条件を満たしていないタスクは、サーバーの既定のリソース プールに割り当てられます。  
  
     リソース ガバナーが分類子関数を使用してリソース プールを決定するように指定することから始めます。 分類子関数のプレースホルダーとして null を割り当てることができます。  
  
    ```  
    ALTER RESOURCE GOVERNOR WITH (classifier_function = NULL);  
    ALTER RESOURCE GOVERNOR reconfigure;  
    ```  
  
     詳細については、「[ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)」を参照してください。  
  
2.  各リソース プール用の分類子関数には、そのリソース プールに割り当てる必要があるステートメントまたは受信要求の種類を定義します。  
  
     たとえば、次の関数は、要求を送信したアプリケーションが 'Microsoft R Host' または 'RStudio' の場合は、ユーザー定義の外部リソース プールに割り当てられたスキーマの名前を返します。それ以外の場合は既定のリソース プールを返します。  
  
    ```  
    USE master  
    GO  
    CREATE FUNCTION is_ds_apps()  
    RETURNS sysname  
    WITH schemabinding  
    AS  
    BEGIN  
        IF program_name() in ('Microsoft R Host', 'RStudio') RETURN 'ds_wg';  
        RETURN 'default'  
        END;  
    GO  
    ```  
  
3.  関数を作成したら、リソース グループを再定義して、新しい分類子関数が先ほど定義した外部リソース グループに割り当てられるようにします。  
  
    ```  
    ALTER RESOURCE GOVERNOR WITH  (classifier_function = dbo.is_ds_apps);  
    ALTER RESOURCE GOVERNOR WITH reconfigure;  
    go  
    ```  
  
## <a name="verify-new-resource-pools-and-affinity"></a>新しいリソース プールとアフィニティを確認する  
  
1.  変更されたことを確認するには、すべてのインスタンスのリソース プール ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サーバーの既定のプール、外部プロセス用の既定のリソース プール、および外部プロセス用のユーザー定義プール) に関連付けられているワークロード グループのサーバーのメモリと CPU の構成を調べます。  
  
    ```  
    SELECT * FROM sys.resource_governor_workload_groups;  
    ```  

    **結果**

    |group_id|name|importance|request_max_memory_grant_percent|request_max_cpu_time_sec|request_memory_grant_timeout_sec|max_dop|group_max_requests pool_id|pool_idd|external_pool_idd|  
    |-|-|-|-|-|-|-|-|-|-|  
    |1|internal|Medium|25|0|0|0|0|1|2|  
    |2|既定値 (default)|Medium|25|0|0|0|0|2|2|  
    |256|ds_wg|Medium|25|0|0|0|0|2|256|  
  
2.  新しいカタログ ビュー [sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md) を使用して、すべての外部リソース プールを表示できます。  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pools;  
    ```  
    **結果**
    
    |external_pool_id|name|max_cpu_percent|max_memory_percent|max_processes|version|  
    |-|-|-|-|-|-|  
    |2|既定値 (default)|100|20|0|2|  
    |256|ds_ep|100|40|0|1|  
  
     詳細については、「[Resource Governor Catalog Views &#40;Transact-SQL&#41; (リソース ガバナーのカタログ ビュー (Transact-SQL))](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)」を参照してください。  
  
3.  次のステートメントは、外部のリソース プールに関連付けられたコンピューター リソースに関する情報を返します。  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pool_affinity;  
    ```  
  
     ここでは、プールは、AUTO のアフィニティで作成されたため、情報は表示されません。 詳細については、「 [sys.dm_resource_governor_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)   
 [ R Services 用のリソース管理](../../advanced-analytics/r-services/resource-governance-for-r-services.md)  
  
  

