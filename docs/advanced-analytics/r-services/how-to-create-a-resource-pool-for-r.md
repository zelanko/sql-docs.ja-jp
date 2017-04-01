---
title: "R のリソース プールを作成する方法 | Microsoft Docs"
ms.custom: ""
ms.date: "10/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c7f7f6e4-774d-4b45-b94a-f06c51718475
caps.latest.revision: 19
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 19
---
# R のリソース プールを作成する方法
  このトピックでは、R のワークロードを管理するためには、具体的には、リソース プールを作成する方法について説明 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]します。 R サービス (データベース) を既にインストールしているし、再構成することが前提としています、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] R. で使用したリソースのより細かい管理をサポートするためにインスタンス  
  
 サーバー リソースの管理の詳細については、次を参照してください。 [リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md) と [リソース ガバナー関連の動的管理ビューと #40 です。Transact SQL と #41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)します。  
  
 **手順**  
  
1.  既存のリソース プールのステータスを確認します。  
  
2.  サーバー リソース プールを変更します。  
  
3.  外部プロセス用に新しいリソース プールを作成します。  
  
4.  R の要求を識別する分類子関数を作成します。  
  
5.  新しい外部のリソース プールが R のジョブをキャプチャしていることを確認します。  
  
##  <a name="bkmk_ReviewStatus"></a> 既存のリソース プールの状態を確認します。  
  
1.  最初に、サーバーの既定のプールに割り当てられたリソースを確認してください。  
  
    ```  
    SELECT * FROM sys.resource_governor_resource_pools WHERE name = 'default'  
    ```  
     **[結果]**

    |pool_id|name|min_cpu_percent|max_cpu_percent|min_memory_percent|max_memory_percent|cap_cpu_percent|min_iops_per_volume|max_iops_per_volume|  
    |-|-|-|-|-|-|-|-|-|  
    |2|既定値 (default)|0|100|0|100|100|0|0|  

2.  既定値に割り当てられているリソースを確認して **外部** リソース プールです。  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pools WHERE name = 'default'  
    ```  
     
    **[結果]**

    |external_pool_id|name|max_cpu_percent|max_memory_percent|max_processes|version|  
    |-|-|-|-|-|-|  
    |2|既定値 (default)|100|20|0|2|  
 
3.  、これらのサーバーの既定の設定で、R のランタイムをリソース不足のため、ほとんどのタスクを完了するがあります。 これを変更するには、ようにサーバー リソース使用率を変更する必要があります。  
  
    -   使用できる、コンピューターの最大メモリを減らす [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
    -   外部プロセスで使用できる最大のコンピューターのメモリを増やす  
  
## サーバー リソース使用率を変更します。  
  
1.   [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], を制限するには、次のステートメントを実行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メモリ使用量を **60%** 'max server memory' 設定の値。  
  
    ```  
    ALTER RESOURCE POOL "default" WITH (max_memory_percent = 60);  
    ```  
  
2.  同様に、外部プロセスでメモリの使用を制限するのには、次のステートメントを実行 **40%** 合計コンピューター リソースのです。  
  
    ```  
    ALTER EXTERNAL RESOURCE POOL "default" WITH (max_memory_percent = 40);  
    ```  
  
3.  がこれらの変更を適用するのには、再構成し、次のようにリソース ガバナーを再起動する必要があります。  
  
    ```  
    ALTER RESOURCE GOVERNOR reconfigure;  
    ```  
  
    > [!NOTE]  
    >  これらは、単に推奨される設定 (;) で開始するにはR に対して他のサーバー プロセスを判断する要件、環境とワークロードのバランスを評価する必要があります。  
  
## ユーザー定義の外部リソース プールを作成します。  
  
1.  リソース ガバナーの構成の変更内容は、サーバー全体にわたって適用され、外部のプールを使用するワークロードと同様に、サーバーの既定のプールを使用するワークロードに影響します。  
  
     そのため、ワークロードが優先順位を持つより細かい制御を提供するには、新しいユーザー定義の外部リソース プールを作成できます。 また、分類子関数を定義して、外部のリソース プールに割り当てる必要があります。  
  
     新しいを作成して開始 *ユーザー定義の外部リソース プール*します。 次の例では、プールの名前 **ds_ep**します。  
  
    ```  
    CREATE EXTERNAL RESOURCE POOL ds_ep WITH (max_memory_percent = 40);  
    ```  
  
     新しいメモ **外部** キーワードです。  
  
2.  という名前のワークロード グループを作成する `ds_wg` セッション要求の管理に使用します。 既定のプールを使用する SQL クエリクエリを使用するすべての外部プロセスで、 `ds_ep` プールです。  
  
    ```  
    CREATE WORKLOAD GROUP ds_wg WITH (importance = medium) USING "default", EXTERNAL "ds_ep";  
    ```  
  
     要求は、要求を分類することはできません、またはその他の分類エラーがある場合、既定のグループに割り当てられます。  
  
     詳細については、次を参照してください。 [リソース ガバナー ワークロード グループ](../../relational-databases/resource-governor/resource-governor-workload-group.md) と [ワークロード グループの作成と #40 です。Transact SQL と #41;](../../t-sql/statements/create-workload-group-transact-sql.md)します。  
  
## R の分類子関数を作成します。  
  
1.  分類子関数では、受信タスクを検査し、タスクは、いずれかの現在のリソース プールを使用して実行できるかどうかを決定します。 分類関数の条件を満たしていないタスクは、サーバーの既定のリソース プールに割り当てられます。  
  
     分類子関数を使用することによってリソース ガバナー リソース プールを指定することで開始します。 分類子関数のプレース ホルダーとして null を割り当てることができます。  
  
    ```  
    ALTER RESOURCE GOVERNOR WITH (classifier_function = NULL);  
    ALTER RESOURCE GOVERNOR reconfigure;  
    ```  
  
     詳細については、「[ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)」を参照してください。  
  
2.  各リソース プールの分類子関数では、ステートメントまたはリソース プールに割り当てる必要が受信要求の種類を定義します。  
  
     たとえば、次の関数が要求を送信したアプリケーションが ' Microsoft R Host' または 'RStudio'; の場合は、ユーザー定義の外部リソース プールに割り当てられているスキーマの名前を返しますそれ以外の場合、既定のリソース プールを返します。  
  
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
  
3.  関数が作成されると、新しい分類子関数を前に定義した外部のリソース グループに割り当てるリソース グループを再構成します。  
  
    ```  
    ALTER RESOURCE GOVERNOR WITH  (classifier_function = dbo.is_ds_apps);  
    ALTER RESOURCE GOVERNOR WITH reconfigure;  
    go  
    ```  
  
## 新しいリソース プールとの類似性を確認します。  
  
1.  変更が加えられたことを確認するには、各インスタンスのすべてのリソース プールに関連付けられているワークロード グループのサーバーのメモリと CPU の構成を調べます。 の既定のプール、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サーバー、外部プロセスの既定のリソース プール、およびユーザー定義のプールは、外部プロセスです。  
  
    ```  
    SELECT * FROM sys.resource_governor_workload_groups;  
    ```  

    **[結果]**

    |group_id|name|importance|request_max_memory_grant_percent|request_max_cpu_time_sec|request_memory_grant_timeout_sec|max_dop|group_max_requests pool_id|pool_idd|external_pool_idd|  
    |-|-|-|-|-|-|-|-|-|-|  
    |1|内部|Medium|25|0|0|0|0|1|2|  
    |2|既定値 (default)|Medium|25|0|0|0|0|2|2|  
    |256|ds_wg|Medium|25|0|0|0|0|2|256|  
  
2.  新しいカタログ ビューを使用する [sys.resource_governor_external_resource_pools & #40 です。Transact SQL と #41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md), 、すべての外部のリソース プールを表示します。  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pools;  
    ```  
    **[結果]**
    
    |external_pool_id|name|max_cpu_percent|max_memory_percent|max_processes|version|  
    |-|-|-|-|-|-|  
    |2|既定値 (default)|100|20|0|2|  
    |256|ds_ep|100|40|0|1|  
  
     詳細については、次を参照してください。 [リソース ガバナーのカタログ ビューと #40 です。Transact SQL と #41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)します。  
  
3.  次のステートメントは、外部のリソース プールに関連付けられ、コンピューター リソースに関する情報を返します。  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pool_affinity;  
    ```  
  
     この場合、プールは、AUTO アフィニティで作成された、ため情報は表示されません。 詳細については、次を参照してください。 [sys.dm_resource_governor_resource_pool_affinity & #40 です。Transact SQL と #41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md)します。  
  
## 参照  
 [リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)   
 [R のサービスのリソース管理](../../advanced-analytics/r-services/resource-governance-for-r-services.md)  
  
  