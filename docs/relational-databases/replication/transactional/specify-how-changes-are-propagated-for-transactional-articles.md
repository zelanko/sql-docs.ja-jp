---
title: "トランザクション アーティクルに変更を反映する方法の指定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "トランザクション レプリケーション, 反映方法"
ms.assetid: a10c5001-22cc-4667-8f0b-3d0818dca2e9
caps.latest.revision: 48
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# トランザクション アーティクルに変更を反映する方法の指定
  トランザクション レプリケーションを使用すると、パブリッシャーからサブスクライバーに変更を反映する方法を指定できます。 パブリッシュされた各テーブルに対して、次の 4 つの方法のいずれかを指定して、各操作 (INSERT、UPDATE、または DELETE) をサブスクライバーに反映できます。  
  
-   トランザクション レプリケーションのスクリプトを作成し、その後、ストアド プロシージャを呼び出して変更をサブスクライバーに反映するように指定します (既定値)。  
  
-   INSERT、UPDATE、または DELETE ステートメントを使用して、変更が反映されるように指定します ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーの既定値)。  
  
-   カスタム ストアド プロシージャを使用するように指定します。  
  
-   この操作がサブスクライバーで実行されないように指定します。 その種類のトランザクションはレプリケートされません。  
  
 既定では、トランザクション レプリケーションが、各サブスクライバーにインストールされているストアド プロシージャのセットを使用して、変更をサブスクライバーに伝達します。 パブリッシャーでテーブルに挿入、更新、または削除が発生した場合、各操作はサブスクライバーでのストアド プロシージャへの呼び出しに翻訳されます。 ストアド プロシージャは、テーブル内の列にマップされるパラメーターを受け入れ、それらの列がサブスクライバーで変更されることを許可します。  
  
 データの変更をトランザクション アーティクルに反映する方法を設定するを参照してください。 [トランザクション アーティクルへのデータ変更の伝達方法を設定](../../../relational-databases/replication/publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md)します。  
  
## 既定のストアド プロシージャとカスタム ストアド プロシージャ  
 各テーブル アーティクルに対して、既定でレプリケーションによって作成されるのは、次の 3 つのプロシージャです。  
  
-   **sp_msins _ \<** *tablename* **>**, 、挿入処理します。  
  
-   **sp_msupd _ \<** *tablename* **>**, 、更新処理します。  
  
-   **sp_msdel _ \<** *tablename* **>**, 、削除を処理します。  
  
  **\<***Tablename***>** で使用される手順は、アーティクルをパブリケーションに追加された方法と、サブスクリプション データベースが別の所有者を持つ同じ名前のテーブルを含むかどうかによって異なります。  
  
 これらのすべてのプロシージャは、パブリケーションにアーティクルを追加するときに指定したカスタム プロシージャと置き換えることができます。 カスタム プロシージャは、サブスクライバーでの行の更新時にデータを監査テーブルに挿入するなど、アプリケーションにカスタム ロジックが必要な場合に使用されます。 カスタム ストアド プロシージャの指定の詳細については、上記のトピックを参照してください。  
  
 既定のレプリケーション プロシージャまたはカスタム プロシージャを指定した場合は、各プロシージャに対する呼び出し構文も指定します (既定のプロシージャを使用する場合は、レプリケーションによって既定値が選択されます)。 呼び出し構文によって、プロシージャに提供されたパラメーターの構造、および各データの変更と共にサブスクライバーに送信される情報の量が決定されます。 詳細については、このトピックの「ストアド プロシージャの呼び出し構文」を参照してください。  
  
### カスタム ストアド プロシージャの使用に関する注意点  
 カスタム ストアド プロシージャを使用する場合は、次の点に注意してください。  
  
-   ストアド プロシージャ内でロジックをサポートする必要があります。[!INCLUDE[msCoName](../../../includes/msconame-md.md)] はカスタム ロジックをサポートしていません。  
  
-   レプリケーションによって使用されるトランザクションの競合を防ぐため、カスタム プロシージャでは明示的なトランザクションを使用しないでください。  
  
-   サブスクライバーにおけるスキーマは、通常、パブリッシャーにおけるスキーマと同一になりますが、列フィルターが使用されている場合は、パブリッシャーのスキーマのサブセットにすることもできます。 ただし、としてスキーマを変換する必要がある場合、データを移動、サブスクライバーでスキーマがパブリッシャーで、スキーマのサブセットではないように [!INCLUDE[ssISCurrent](../../../includes/ssiscurrent-md.md)] 推奨されるソリューションです。 詳細については、次を参照してください。 [SQL Server Integration Services](../../../integration-services/sql-server-integration-services.md)します。  
  
-   スキーマの変更をパブリッシュされたテーブルに加える場合は、カスタム プロシージャを再生成する必要があります。 詳細については、次を参照してください。 [再生成するカスタム トランザクション プロシージャのスキーマ変更の反映](../../../relational-databases/replication/transactional/regenerate-custom-transactional-procedures-to-reflect-schema-changes.md)します。  
  
-   1 より大きい値を使用する場合 **- SubscriptionStreams** ディストリビューション エージェントのパラメーターは、主キー列に対する更新が成功したこと確認する必要があります。 例:  
  
    ```  
    update ... set pk = 2 where pk = 1 -- update 1  
    update ... set pk = 3 where pk = 2 -- update 2  
    ```  
  
     ディストリビューション エージェントが複数の接続を使用する場合、次の 2 つの更新は、さまざまな接続を経由してレプリケートされる可能性があります。 最初に update 1 が適用される場合は、問題は発生しません。最初に update 2 が適用された場合は、update 1 がまだ発生していないため、"0 行処理されました" というメッセージが返されます。 既定のプロシージャでは、更新による影響を受ける行がない場合にエラーを発生させることによって、このような状況を処理します。  
  
    ```  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sys.sp_MSreplraiserror 20598  
    ```  
  
     エラーの発生によって、ディストリビューション エージェントでは単一の接続による更新の再試行が強制的に行われ、この処理は正常に実行されます。 カスタム ストアド プロシージャには、これと同様のロジックを含める必要があります。  
  
### ストアド プロシージャの呼び出し構文  
 トランザクション レプリケーションで使用されるプロシージャを呼び出すために使用される構文には、5 つのオプションがあります。  
  
-   CALL 構文。 挿入、更新、および削除に使用できます。 既定では、レプリケーションは挿入と削除に対してこの構文を使用します。  
  
-   SCALL 構文。 更新のみに使用できます。 既定では、レプリケーションは更新に対してこの構文を使用します。  
  
-   MCALL 構文。 更新のみに使用できます。  
  
-   XCALL 構文。 更新と削除に使用できます。  
  
-   VCALL。 更新可能なサブスクリプションに対して使用されます。 内部使用のみです。  
  
 サブスクライバーに反映されるデータの量は、各方法で異なります。 たとえば、SCALL は、更新によって実際に影響を受ける列だけに対する値の中でデータを渡します。 対照的に、XCALL は、更新によって影響を受けるかどうかに関係なくすべての列、および各列のすべての古いデータ値を必要とします。 多くの場合、SCALL は更新に適していますが、アプリケーションが更新中にすべてのデータ値を必要とする場合は、XCALL を更新に対して使用することもできます。  
  
#### CALL 構文  
 INSERT ストアド プロシージャ  
 INSERT ステートメントを処理するストアド プロシージャには、すべての列に挿入する値が渡されます。  
  
```  
c1, c2, c3,... cn  
```  
  
 UPDATE ストアド プロシージャ  
 UPDATE ステートメントを処理するストアド プロシージャには、アーティクルで定義されているすべての列を更新する値、およびその後に主キー列の元の値が渡されます (どの列が変更されたかは、判別されません)。  
  
```  
c1, c2, c3,... cn, pkc1, pkc2, pkc3,... pkcn  
```  
  
 DELETE ストアド プロシージャ  
 DELETE ステートメントを処理するストアド プロシージャには、主キー列の値が渡されます。  
  
```  
pkc1, pkc2, pkc3,... pkcn  
```  
  
#### SCALL 構文  
 UPDATE ストアド プロシージャ  
 UPDATE ステートメントを処理するストアド プロシージャに変更が、主キー列の元の値を続けて、ビットマスク列のみを更新する値を渡す (**binary (n)**) 変更された列を示すパラメーターです。 次の例では、列 2 (c2) は変更されていません。  
  
```  
c1, , c3,... cn, pkc1, pkc2, pkc3,... pkcn, bitmask  
```  
  
#### MCALL 構文  
 UPDATE ストアド プロシージャ  
 UPDATE ステートメントを処理するストアド プロシージャにビットマスクの主キー列の元の値の後に、この記事で定義されているすべての列を更新する値を渡す (**binary (n)**) 変更された列を示すパラメーターです。  
  
```  
c1, c2, c3,... cn, pkc1, pkc2, pkc3,... pkcn, bitmask  
```  
  
#### XCALL 構文  
 UPDATE ストアド プロシージャ  
 UPDATE ステートメントを処理するストアド プロシージャには、アーティクルで定義されているすべての列の元の値 (前イメージ) が渡され、その後にアーティクルで定義されているすべての列の更新された値 (後イメージ) が渡されます。  
  
```  
old-c1, old-c2, old-c3,... old-cn, c1, c2, c3,... cn,  
```  
  
 DELETE ストアド プロシージャ  
 DELETE ステートメントを処理するストアド プロシージャには、アーティクルで定義されているすべての列の元の値 (前イメージ) が渡されます。  
  
```  
old-c1, old-c2, old-c3,... old-cn  
```  
  
> [!NOTE]  
>  XCALL を使用する場合前イメージ値に、 **テキスト** と **イメージ** 列が NULL として予想されます。  
  
## 使用例  
 次のプロシージャは、[!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] サンプル データベース内の `Vendor Table` に対して作成された既定のプロシージャです。  
  
```  
--INSERT procedure using CALL syntax  
create procedure [sp_MSins_PurchasingVendor]   
  @c1 int,@c2 nvarchar(15),@c3 nvarchar(50),@c4 tinyint,@c5 bit,@c6 bit,@c7 nvarchar(1024),@c8 datetime  
as   
begin   
insert into [Purchasing].[Vendor]([VendorID]  
,[AccountNumber]  
,[Name]  
,[CreditRating]  
,[PreferredVendorStatus]  
,[ActiveFlag]  
,[PurchasingWebServiceURL]  
,[ModifiedDate])  
values (   
 @c1  
,@c2  
,@c3  
,@c4  
,@c5  
,@c6  
,@c7  
,@c8  
 )   
end  
go  
  
--UPDATE procedure using SCALL syntax  
create procedure [sp_MSupd_PurchasingVendor]   
 @c1 int = null,@c2 nvarchar(15) = null,@c3 nvarchar(50) = null,@c4 tinyint = null,@c5 bit = null,@c6 bit = null,@c7 nvarchar(1024) = null,@c8 datetime = null,@pkc1 int  
,@bitmap binary(2)  
as  
begin  
update [Purchasing].[Vendor] set   
 [AccountNumber] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [AccountNumber] end  
,[Name] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [Name] end  
,[CreditRating] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [CreditRating] end  
,[PreferredVendorStatus] = case substring(@bitmap,1,1) & 16 when 16 then @c5 else [PreferredVendorStatus] end  
,[ActiveFlag] = case substring(@bitmap,1,1) & 32 when 32 then @c6 else [ActiveFlag] end  
,[PurchasingWebServiceURL] = case substring(@bitmap,1,1) & 64 when 64 then @c7 else [PurchasingWebServiceURL] end  
,[ModifiedDate] = case substring(@bitmap,1,1) & 128 when 128 then @c8 else [ModifiedDate] end  
where [VendorID] = @pkc1  
if @@rowcount = 0  
    if @@microsoftversion>0x07320000  
        exec sp_MSreplraiserror 20598  
end  
go  
  
--DELETE procedure using CALL syntax  
create procedure [sp_MSdel_PurchasingVendor]   
  @pkc1 int  
as   
begin   
delete [Purchasing].[Vendor]  
where [VendorID] = @pkc1  
if @@rowcount = 0  
    if @@microsoftversion>0x07320000  
        exec sp_MSreplraiserror 20598  
end   
go  
```  
  
## 参照  
 [トランザクション レプリケーションのアーティクル オプション](../../../relational-databases/replication/transactional/article-options-for-transactional-replication.md)  
  
  