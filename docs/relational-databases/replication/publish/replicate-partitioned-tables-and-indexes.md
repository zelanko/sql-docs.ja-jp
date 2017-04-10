---
title: "パーティション テーブルとパーティション インデックスのレプリケート | Microsoft Docs"
ms.custom: ""
ms.date: "09/10/2015"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "パーティション インデックス [SQL Server]、レプリケート"
  - "パーティション テーブル [SQL Server]、レプリケート"
  - "レプリケーション [SQL Server]、パーティション テーブル"
  - "パブリッシング [SQL Server レプリケーション]、パーティション テーブル"
  - "トランザクション レプリケーション、パーティション テーブル"
ms.assetid: c9fa81b1-6c81-4c11-927b-fab16301a8f5
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# パーティション テーブルとパーティション インデックスのレプリケート
  大きなテーブルやインデックスをパーティション分割すると、データのサブセットに対するアクセスや管理を迅速かつ効率的に行うと同時に、データ コレクションの整合性を維持することができるので、大きなテーブルやインデックスを管理しやすくなります。 詳細については、「 [Partitioned Tables and Indexes](../../../relational-databases/partitions/partitioned-tables-and-indexes.md)」を参照してください。 レプリケーションでは、パーティション テーブルとパーティション インデックスを扱う方法を指定するプロパティ セットによって、パーティション分割をサポートします。  
  
## トランザクション レプリケーションおよびマージ レプリケーションのアーティクルのプロパティ  
 次の表に、データのパーティション分割に使用されるオブジェクトを示します。  
  
|オブジェクト|作成に使用するステートメント|  
|------------|----------------------|  
|パーティション テーブルまたはパーティション インデックス|CREATE TABLE または CREATE INDEX|  
|パーティション関数|CREATE PARTITION FUNCTION|  
|パーティション構成|CREATE PARTITION SCHEME|  
  
 パーティション分割に関連するプロパティの最初のセットは、パーティション分割するオブジェクトをサブスクライバーにコピーするかどうかを指定するアーティクルのスキーマ オプションです。 これらのスキーマ オプションは次の方法で設定できます。  
  
-   パブリケーションの新規作成ウィザードの **[アーティクルのプロパティ]** ページ、または [パブリケーションのプロパティ] ダイアログ ボックス。 上記の表に示したオブジェクトをコピーするには、 **[テーブル分割構成のコピー]** プロパティと **[インデックス分割構成のコピー]** プロパティに、値 **true**を指定します。 アクセスする方法については、 **アーティクルのプロパティ** を参照してください] ページで、 [パブリケーション プロパティの変更を表示および](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)です。  
  
-   使用して、 *schema_option* 次のストアド プロシージャの 1 つのパラメーター。  
  
    -   [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) または [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md) トランザクション レプリケーション  
  
    -   [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) または [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) マージ レプリケーション  
  
     上記の表に示したオブジェクトをコピーするには、適切なスキーマ オプション値を指定します。 スキーマ オプションを指定する方法については、「 [Specify Schema Options](../../../relational-databases/replication/publish/specify-schema-options.md)」を参照してください。  
  
 レプリケーションでは、初期同期中にオブジェクトがサブスクライバーにコピーされます。 パーティション構成で PRIMARY 以外のファイル グループを使用する場合、そのファイル グループは初期同期の前にサブスクライバーに存在している必要があります。  
  
 サブスクライバーが初期化された後、データ変更がサブスクライバーに反映され、適切なパーティションに適用されます。 ただし、パーティション構成に対する変更はサポートされていません。 トランザクション レプリケーションとマージ レプリケーションでは、ALTER PARTITION FUNCTION コマンド、ALTER PARTITION SCHEME コマンド、ALTER INDEX コマンドの REBUILD WITH PARTITION ステートメントのレプリケートはサポートされません。 これらに関連付けられた変更は、サブスクライバーに自動的にレプリケートされません。 ユーザーがサブスクライバー側で同様の変更を手動で行う必要があります。  
  
## レプリケーションによるパーティション切り替えのサポート  
 テーブル分割の主な利点の 1 つは、パーティション間でデータのサブセットをすばやく効率的に移動できることです。 データは SWITCH PARTITION コマンドを使用して移動します。 既定では、テーブルのレプリケーションが有効な場合、SWITCH PARTITION 操作は次の理由でブロックされます。  
  
-   パブリッシャーに存在するテーブルを移動元または移動先としてデータを移動する場合に、そのデータがサブスクライバーに存在しないと、パブリッシャーとサブスクライバーの間で不整合が発生します。 この問題は、一般に、ステージング テーブルにかかわるデータの移動で発生します。  
  
-   サブスクライバーにパブリッシャーとは異なるパーティション テーブルの定義がある場合、ディストリビューション エージェントが変更をサブスクライバーに適用しようとすると失敗します。  
  
 このような問題が発生する可能性はありますが、トランザクション レプリケーションでパーティション切り替えを有効にすることができます。 パーティション切り替えを有効にする前に、パーティション切り替えに関連するすべてのテーブルがパブリッシャーとサブスクライバーに存在し、テーブル定義およびパーティション定義が同じであることを確認してください。  
  
 パーティションがある場合は、パブリッシャーやサブスクライバーをオンにする、まったく同じパーティション構成 *allow_partition_switch* と共に *replication_partition_switch* パーティション切り替えステートメントをサブスクライバーにレプリケートすることだけができます。 にすることもできます。 *allow_partition_switch* DDL をレプリケートしないでします。 これは、過去の月をパーティションからロール アウトする一方、バックアップの目的で、レプリケートしたパーティションをサブスクライバーにもう 1 年保持する場合に便利です。  
  
 SQL Server 2008 R2 から現在のバージョンまででパーティション切り替えを有効にすると、近い将来、分割操作とマージ操作が必要になる可能性があります。 レプリケートされたテーブルでの分割またはマージ操作を実行する前に、該当するパーティションに保留中のレプリケートされたコマンドがないことを確認します。 分割操作とマージ操作中にパーティションで DML 操作が実行されないようにする必要もあります。 ログ リーダーが処理していないトランザクションがある場合や、分割操作またはマージ操作中に、レプリケートされたテーブルのパーティションで DML 操作が実行される場合 (同じパーティションに関連する場合)、ログ リーダー エージェントで処理エラーが発生する可能性があります。 このエラーを修正するには、サブスクリプションの再初期化が必要になる場合があります。  
  
> [!WARNING]  
>  ピア ツー ピア パブリケーションでは、非表示の列が競合の検出および解決のために使用されるため、パーティション切り替えを有効にしないでください。  
  
### パーティション切り替えの有効化  
 トランザクション パブリケーションの次のプロパティを使用すると、レプリケーション環境でのパーティション切り替えの動作を制御できます。  
  
-   **@allow_partition_switch**, に設定すると **true**, 、パブリケーション データベースに対して SWITCH PARTITION を実行することができます。  
  
-   **@replicate_partition_switch** スイッチ パーティション DDL ステートメントがサブスクライバーにレプリケートされるかどうかを判断します。 このオプションは、有効な場合にのみ **@allow_partition_switch** に設定されている **true**します。  
  
 使用してこれらのプロパティを設定する [sp_addpublication](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md) パブリケーションが作成されると、またはを使用して [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) パブリケーションを作成した後です。 既に述べたとおり、マージ レプリケーションではパーティション切り替えがサポートされません。 マージ レプリケーションが有効になっているテーブルで SWITCH PARTITION を実行するには、パブリケーションからテーブルを削除します。  
  
## 参照  
 [データとデータベース オブジェクトのパブリッシュ](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  