---
title: "Oracle パブリッシャーの設計上の注意点および制限 | Microsoft Docs"
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
  - "Oracle パブリッシング [SQL Server replication], 設計上の注意点と制限"
ms.assetid: 8d9dcc59-3de8-4d36-a61f-bc3ca96516b6
caps.latest.revision: 48
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 48
---
# Oracle パブリッシャーの設計上の注意点および制限
  Oracle データベースからの発行がからの発行にほぼ同じように機能するように設計、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースです。 ただし、以下の制限および問題に注意してください。  
  
-   [Oracle (ゲートウェイ)] を選択すると、[Oracle (完全)] より高いパフォーマンスが得られますが、このオプションは、複数のトランザクション パブリケーションで同じテーブルをパブリッシュする場合は使用できません。 テーブルを表示できるのは、最大で 1 つのトランザクション パブリケーションと、任意の数のスナップショット パブリケーションになります。 複数のトランザクション パブリケーションで同じテーブルをパブリッシュする必要がある場合は、[Oracle (完全)] を選択します。  
  
-   レプリケーションでは、テーブル、インデックス、および具体化されたビューのパブリッシュをサポートしています。 その他のオブジェクトはレプリケートされません。  
  
-   Oracle と [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のデータベースのデータの保存および処理には、レプリケーションに影響を与える小さな違いがいくつかあります。  
  
-   Oracle パブリッシャーを使用する場合に、トランザクション レプリケーション機能をサポートする方法にはさまざまな違いがあります。  
  
## Oracle からのオブジェクトのパブリッシュのサポート  
 レプリケーションでは、Oracle データベースからの以下のオブジェクトのレプリケートをサポートしています。  
  
-   テーブル  
  
-   索引構成表  
  
-   インデックス  
  
-   具体化されたビュー (テーブルとしてレプリケート)  
  
 以下については、パブリッシュされたテーブルに存在する可能性はありますが、レプリケートされません。  
  
-   ドメイン ベースのインデックス  
  
-   関数ベースのインデックス  
  
-   既定値  
  
-   CHECK 制約  
  
-   外部キー  
  
-   ストレージのオプション (テーブルスペース、クラスターなど)  
  
 以下のオブジェクトはレプリケートできません。  
  
-   入れ子になったテーブル  
  
-   ビュー  
  
-   パッケージ、パッケージ本体、プロシージャ、およびトリガー  
  
-   キュー  
  
-   シーケンス  
  
-   シノニム  
  
 サポートされているデータ型については、次を参照してください。 [Oracle パブリッシャーのデータ型マッピング](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)します。  
  
## Oracle と SQL Server の違い  
  
-   Oracle では、一部のオブジェクトに対する最大サイズ制限が異なります。 Oracle パブリケーション データベースで作成されたオブジェクトは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の対応するオブジェクトの最大サイズ制限に従う必要があります。 制限については [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], を参照してください [SQL Server の最大容量仕様](../../../sql-server/maximum-capacity-specifications-for-sql-server.md)します。  
  
-   既定では、Oracle のオブジェクト名は大文字で作成されます。 Oracle オブジェクトの名前が Oracle データベースで大文字となっている場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターでこれらをパブリッシュするときは、名前が大文字になっているかどうかを確認してください。 大文字および小文字を正しく指定しないと、オブジェクトが見つからないことを示すエラー メッセージが表示される可能性があります。  
  
-   Oracle の SQL 言語仕様は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] と若干異なります。行フィルターは、Oracle 準拠の構文で記述する必要があります。  
  
### ラージ オブジェクトに関する注意点  
 ラージ オブジェクト (LOB) データは、アーティクルのログ テーブルに格納されません。LOB データへの更新は、常に、パブリッシュされたテーブルから直接取得します。 更新がトランザクション パブリケーションでレプリケートされるのは、LOB に影響を与える操作により、レプリケートされたテーブルでレプリケーション トリガーが起動される場合に限られます。 Oracle トリガーは、LOB を含む行が挿入または削除されると起動されますが、LOB の列への更新の場合には、トリガーは起動されません。 LOB の列への更新が直ちにレプリケートされるのは、同じ行の LOB ではない列も同じ Oracle トランザクションで更新される場合に限られます。 更新されない場合、LOB の列は、同じ行の LOB ではない列への更新が次回に発生したときに、サブスクライバーで更新されます。 アプリケーションでこの動作を許容できることを確認してください。  
  
 トランザクション パブリケーションで LOB の列への更新をレプリケートするには、アプリケーションを記述するときに、次のいずれかの方法を検討してください。  
  
-   行を更新せず、トランザクションで行を削除および再挿入します。行を再挿入するときは、新しい LOB を指定します。 削除と挿入の両方でトリガーを起動するため、行はレプリケートされます。  
  
-   LOB の列に加え、LOB ではない列を行の更新に含めるか、同じ Oracle トランザクションの一部として、その行の LOB ではない列を更新します。 どちらの場合でも、LOB ではない列の更新により、トリガーが起動します。  
  
 Lob の詳細については、次を参照してください。 [Oracle パブリッシャーのデータ型マッピング](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)します。  
  
### 一意インデックスと制約  
 スナップショット レプリケーションとトランザクション レプリケーションの両方において、一意のインデックスおよび制約 (主キー制約を含む) に含まれる列は、特定の制限事項に従う必要があります。 これらの制限に従わない場合、制約またはインデックスはレプリケートされません。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインデックスに許容される最大列数は 16 です。  
  
-   一意の制約に含まれるすべての列は、サポートされているデータ型である必要があります。 データ型の詳細については、次を参照してください。 [Oracle パブリッシャーのデータ型マッピング](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)します。  
  
-   一意の制約に含まれるすべての列は、パブリッシュする必要があります (フィルター選択はできません)。  
  
-   一意の制約またはインデックスに関係する列には NULL 値を設定できません。  
  
 以下の問題についても考慮に入れてください。  
  
-   Oracle および [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、NULL の扱いが異なります。Oracle では、NULL を許容する列に NULL 値が指定された複数の行を許可し、一意の制約またはインデックスに含めることができます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 同じ列に対して NULL 値を含む単一行を行だけ許可によって一意性を強制します。 NULL を許容する一意の制約またはインデックスをパブリッシュすることはできません。パブリッシュされたテーブルで、インデックスまたは制約に含まれる列に NULL 値のある行が複数含まれる場合、サブスクライバーで制約違反が発生します。  
  
-   一意性をテストする場合、フィールドの後続の空白は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では無視されますが、Oracle では無視されません。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のトランザクション レプリケーションと同様、Oracle のトランザクション パブリケーションのテーブルには主キーが必要です。主キーは上記のルールに基づき、一意である必要があります。 主キーが前の項目で示したルールに従わない場合、トランザクション レプリケーションに対し、テーブルをパブリッシュすることはできません。  
  
## Oracle パブリッシングと標準的なトランザクション レプリケーションの違い  
  
-   Oracle パブリッシャーは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューター、そのディストリビューターを使用する任意の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] パブリッシャー、またはパブリケーションを受信する任意のサブスクライバーと同じ名前にすることはできません。 同じディストリビューターによって処理される各パブリケーションには、一意の名前を付ける必要があります。  
  
-   Oracle パブリケーションでパブリッシュされたテーブルは、レプリケートされたデータを受信することはできません。 したがって Oracle パブリッシングでは、即時更新サブスクリプションまたはキュー更新サブスクリプションを使用したパブリケーション、およびピア ツー ピア レプリケーションや双方向レプリケーションなど、パブリケーション テーブルがサブスクリプション テーブルとしても機能するトポロジはサポートしていません。  
  
-   Oracle データベースでの主キーから外部キーのリレーションシップは、サブスクライバーにレプリケートされません。 ただし、変更が配信されると、リレーションシップはデータに保持されます。  
  
-   標準的なトランザクション パブリケーションは、最大 1000 列のテーブルをサポートします。 Oracle のトランザクション パブリケーションがサポートするのは 995 列です (レプリケーションにより、パブリッシュされた各テーブルに 5 列が追加されます)。  
  
-   COLLATE 句は、CREATE TABLE ステートメントに追加され、大文字と小文字を区別する比較を有効にします。この比較は、主キーおよび一意の制約にとって重要です。 指定されるスキーマ オプション 0x1000 でこの動作を制御、 **@schema_option** のパラメーター [sp_addarticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)します。  
  
-   ストアド プロシージャを使用して Oracle パブリッシャーを構成またはメンテナンスする場合、プロシージャを明示的なトランザクションに入れないでください。 これは Oracle パブリッシャーへの接続に使用するリンク サーバーではサポートされていません。  
  
-   ウィザードにより Oracle パブリケーションに対するプル サブスクリプションを作成する場合は、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降で提供されたサブスクリプションの新規作成ウィザードを使用する必要があります。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] より古いバージョンの場合でも、ストアド プロシージャおよび SQL-DMO インターフェイスを使用して、Oracle パブリケーションに対するプル サブスクリプションを設定できます。  
  
-   ストアド プロシージャを使用して、サブスクライバーに変更を反映する場合 (既定)、MCALL 構文はサポートされていても、Oracle パブリッシャーからのパブリケーションである場合は、異なる動作をすることに注意してください。 通常、MCALL では、パブリッシャーで更新された列を示すビットマップを提供します。 Oracle パブリケーションの場合、ビットマップは常にすべての列が更新されたことを示しています。 詳細については、ストアド プロシージャを使用して、次を参照してください。 [トランザクション アーティクルに変更を反映する方法を指定](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md)します。  
  
### トランザクション レプリケーション機能のサポート  
  
-   Oracle パブリケーションでは、SQL Server パブリケーションがサポートする一部のスキーマ オプションがサポートされていません。 スキーマ オプションの詳細については、次を参照してください。 [sp_addarticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)します。  
  
-   Oracle パブリケーションに対するサブスクライバーは、即時更新サブスクリプションまたはキュー更新サブスクリプションを使用できません。また、ピア ツー ピア トポロジまたは双方向トポロジでノードになることもできません。  
  
-   Oracle パブリケーションに対するサブスクライバーは、バックアップから自動的に初期化することはできません。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2 つの種類の検証をサポートしています: バイナリと行数。 Oracle パブリッシャーでは、行数検証をサポートしています。 詳細については、次を参照してください。 [レプリケート データの検証](../../../relational-databases/replication/validate-replicated-data.md)します。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2 つのスナップショットの形式を提供しています。 ネイティブ bcp モードとキャラクター モードです。 Oracle パブリッシャーでは、キャラクター モード スナップショットをサポートしています。  
  
-   パブリッシュされた Oracle テーブルへのスキーマ変更はサポートされていません。 スキーマ変更を行うには、まずパブリケーションを削除し、変更を行ってから、パブリケーションおよびサブスクリプションを再作成します。  
  
    > [!NOTE]  
    >  パブリッシュされたテーブルが利用されていないときに、スキーマ変更とその後のパブリケーションおよびサブスクリプションの削除、再作成を一度に行う場合、サブスクリプションに対して [レプリケーションのサポートのみ] オプションを指定できます。 これにより、各サブスクライバーにスナップショットをコピーすることなく、サブスクリプションを同期させることができます。 詳細については、次を参照してください。 [、スナップショット トランザクション サブスクリプションなしの初期化](../../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)します。  
  
### レプリケーションのセキュリティ モデル  
 Oracle のパブリッシングのセキュリティ モデルは、標準的なトランザクション レプリケーションのセキュリティ モデルと同じですが、以下の点が異なります。  
  
-   スナップショット エージェントおよびログ リーダー エージェントがディストリビューターからパブリッシャーへの接続に使用するアカウントは、次のいずれかの方法で指定されます。  
  
    -    **@Security_mode** のパラメーター [sp_adddistpublisher & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md) (の値を指定するも **@login** と **@password** Oracle 認証を使用する場合)  
  
    -    **サーバーへの接続** で Oracle パブリッシャーを構成するときに使用する SQL Server Management Studio] ダイアログ ボックス、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターです。  
  
     標準のトランザクション レプリケーションでは、アカウントが指定されている [sp_addpublication_snapshot & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)  [sp_addlogreader_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)します。  
  
-   する、スナップショット エージェントとログ リーダー エージェントによって接続アカウントを変更することはできません [sp_changedistpublisher & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md) または、シートが、パスワードを変更することができます、プロパティを使用します。  
  
-   1 (Windows 統合認証) の値を指定する場合、 **@security_mode** のパラメーター [sp_adddistpublisher & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md):  
  
    -   プロセス アカウントおよびスナップショット エージェントおよびログ リーダー エージェントの両方で使用するパスワード (、 **@job_login** と **@job_password** のパラメーター [sp_addpublication_snapshot & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)  [sp_addlogreader_agent & #40 です。Transact-SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md))Oracle パブリッシャーに接続するためのパスワードとアカウントと同じである必要があります。  
  
    -   変更することはできません、 **@job_login** パラメーターを通じて [sp_changepublication_snapshot & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md) または [sp_changelogreader_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md), 、パスワードを変更することができます。  
  
 レプリケーションのセキュリティの詳細については、次を参照してください。 [セキュリティと保護と #40 です。レプリケーションと #41;](../../../relational-databases/replication/security/security-and-protection-replication.md)します。  
  
## 参照  
 [Oracle パブリッシャーの管理上の注意点](../../../relational-databases/replication/non-sql/administrative-considerations-for-oracle-publishers.md)   
 [Oracle パブリッシャーの構成](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Oracle パブリッシングの概要](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  