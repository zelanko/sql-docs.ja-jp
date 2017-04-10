---
title: "サブスクリプションの有効期限の設定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "サブスクリプション [SQL Server レプリケーション]、有効期限"
  - "有効期限 [SQL Server レプリケーション]"
  - "保有期間 [SQL Server レプリケーション]"
  - "サブスクリプションの非アクティブ化"
ms.assetid: 542f0613-5817-42d0-b841-fb2c94010665
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# サブスクリプションの有効期限の設定
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、サブスクリプションの有効期限を設定する方法について説明します。 サブスクリプションの期限が切れて削除されるまでの時間は、サブスクリプションの有効期限によって決定されます。 詳しくは、「 [Subscription Expiration and Deactivation](../../../relational-databases/replication/subscription-expiration-and-deactivation.md)」をご覧ください。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [推奨事項](#Recommendations)  
  
-   **サブスクリプションの有効期限を設定するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   サブスクリプションの有効期限は、 *パブリケーション保有期間*とも呼ばれます。 マージ レプリケーション メタデータのクリーンアップは、この設定に依存します。  
  
    -   保有期間が終了するまで、パブリケーションおよびサブスクリプション データベースでメタデータをクリーンアップすることはできません。 レプリケーション パフォーマンスを低下させる可能性があるため、保有期間に大きな値を指定する際は注意してください。 すべてのサブスクライバーが保有期間内で定期的に同期されることを確実に予測できる場合は、小さい値を使用することをお勧めします。  
  
         マージ パブリケーションの保有期間には、異なるタイム ゾーンのサブスクライバーに対応するため、24 時間の猶予期間があります。 たとえば、保有期間を 1 日に設定した場合、実際の保有期間は 48 時間となります。  
  
    -   サブスクリプションの期限が切れないように指定することは可能ですが、メタデータをクリーンアップできなくなるため、この値は使用しないことを強くお勧めします。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 サブスクリプションの有効期限を設定、 **全般** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。  
  
#### サブスクリプションの有効期限を設定するには  
  
1.   **サブスクリプションの有効期限** セクションで、 **全般** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスで、サブスクリプションの有効期限があるかどうかを指定します。  
  
2.  有効期限を設定する場合、有効期限の期間を指定します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 この値は、レプリケーションのストアド プロシージャを使用して、パブリケーションの作成時に設定することも、後で変更することもできます。  
  
#### スナップショットまたはトランザクション パブリケーションのサブスクリプションに対して有効期限を設定するには  
  
1.  パブリッシャーで実行 [sp_addpublication](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)します。 **@retention**にサブスクリプションの有効期限を時間単位で指定します。 既定の有効期限は 336 時間です。 詳しくは、「 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)」をご覧ください。  
  
#### マージ パブリケーションのサブスクリプションに対して有効期限を設定するには  
  
1.  パブリッシャーで実行 [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)します。 **@retention**にサブスクリプションの有効期限を指定します。 有効期間を表現する単位を指定 **@retention_period_unit**, 、次のいずれかを指定することができます。  
  
    -   **1** = 週  
  
    -   **2** = 月  
  
    -   **3** = 年  
  
     既定の有効期限は 14 日です。 詳しくは、「 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)」をご覧ください。  
  
#### スナップショットまたはトランザクション パブリケーションのサブスクリプションに対して有効期限を変更するには  
  
1.  パブリッシャーで実行 [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)します。 **@property** に **retention** を、 **@value**にサブスクリプションの新しい有効期限を時間単位で指定します。  
  
#### マージ パブリケーションのサブスクリプションに対して有効期限を変更するには  
  
1.  パブリッシャーで実行 [sp_helpmergepublication](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), を指定して **@publication** と **@publisher**します。 値に注意してください **retention_period_unit** で結果セットは、次のいずれかになります。  
  
    -   **0** = 日  
  
    -   **1** = 週  
  
    -   **2** = 月  
  
    -   **3** = 年  
  
2.  パブリッシャーで実行 [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)します。 **@property** に **retention** を指定します。また、 **@value**には、手順 1. の保有期間の単位に基づいて、サブスクリプションの新しい有効期限をテキストで指定します。  
  
3.  (省略可能)パブリッシャーで実行 [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)します。 指定 **retention_period_unit** の **@property** と、サブスクリプションの有効期間の新しい単位 **@value**します。  
  
## 参照  
 [レプリケーション システム ストアド プロシージャの概念](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [サブスクリプションの有効期限と非アクティブ化](../../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  