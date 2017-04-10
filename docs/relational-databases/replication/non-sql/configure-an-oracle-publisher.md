---
title: "Oracle パブリッシャーの構成 | Microsoft Docs"
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
  - "Oracle パブリッシング [SQL Server レプリケーション], 構成"
ms.assetid: 240c8416-c8e5-4346-8433-07e0f779099f
caps.latest.revision: 60
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 60
---
# Oracle パブリッシャーの構成
  Oracle パブリッシャーからパブリケーションを作成する方法は、通常のスナップショットおよびトランザクション パブリケーションを作成する方法と同じですが、Oracle パブリッシャーからパブリケーションを作成する前に、次の手順を実行する必要があります (手順 1、3、および 4 については、このトピックで詳しく説明します)。  
  
1.  提供されているスクリプトを使用して Oracle データベース内にレプリケーション管理ユーザーを作成します。  
  
2.  パブリッシュするテーブルに、各テーブルの SELECT 権限を、手順 1. で作成した Oracle 管理ユーザーに対して直接 (ロールを通じてではなく) 許可します。  
  
3.  Oracle クライアント ソフトウェアと OLE DB プロバイダーをインストール、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューター、およびから停止および再起動、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス。 ディストリビューターを 64 ビットのプラットフォームで実行している場合は、64 ビット バージョンの Oracle OLE DB プロバイダーを使用する必要があります。  
  
4.  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターで Oracle データベースをパブリッシャーとして構成します。  
  
 Oracle データベースからレプリケートできるオブジェクトの一覧は、次を参照してください。 [設計に関する考慮事項と Oracle パブリッシャーに対して制限](../../../relational-databases/replication/non-sql/design-considerations-and-limitations-for-oracle-publishers.md)します。  
  
> [!NOTE]  
>  メンバーである必要があります、 **sysadmin** 固定サーバー ロールをパブリッシャーまたはディストリビューターを有効にすると、Oracle パブリケーションから Oracle パブリケーションまたはサブスクリプションを作成します。  
  
## Oracle データベース内でのレプリケーション管理ユーザー スキーマの作成  
 レプリケーション エージェントは、Oracle データベースに接続して、ユーザー スキーマのコンテキストで操作を実行します。このユーザー スキーマは作成する必要があります。 このスキーマには多くの権限を許可する必要があります。この権限については、次のセクションに示します。 このスキーマによって作成されたすべてのオブジェクトを所有している、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] パブリック シノニムを除き、Oracle パブリッシャーのレプリケーション プロセス **MSSQLSERVERDISTRIBUTOR**します。 Oracle データベースで作成されたオブジェクトの詳細については、次を参照してください。 [オブジェクトは、Oracle パブリッシャーで作成](../../../relational-databases/replication/non-sql/objects-created-on-the-oracle-publisher.md)します。  
  
> [!NOTE]  
>  削除する、 **MSSQLSERVERDISTRIBUTOR** パブリック シノニムと構成した Oracle レプリケーション ユーザーを **CASCADE** オプションは、Oracle パブリッシャーからすべてのレプリケーション オブジェクトを削除します。  
  
 Oracle レプリケーション ユーザー スキーマのセットアップに役立つサンプル スクリプトが提供されています。 インストール後に、スクリプトは、次のディレクトリで使用できる [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: *\< ドライブ>*:\\\Program Files\Microsoft SQL Server\\*\< InstanceName>*\MSSQL\Install\oracleadmin.sql します。 トピックにも含まれている [Oracle のアクセス許可を付与するスクリプトを](../../../relational-databases/replication/non-sql/script-to-grant-oracle-permissions.md)します。  
  
 DBA 特権を持つアカウントを使用して Oracle データベースに接続し、スクリプトを実行します。 このスクリプトでは、レプリケーション管理ユーザー スキーマのユーザーとパスワード、およびオブジェクトを作成するときに使用する既定のテーブルスペースの入力が要求されます (このテーブルスペースは Oracle データベース内に存在していることが必要です)。 他のオブジェクトのテーブル スペースの指定方法の詳細については、次を参照してください。 [Oracle テーブル スペースの管理](../../../relational-databases/replication/non-sql/manage-oracle-tablespaces.md)します。 ユーザー名と複雑なパスワードを選択しますが、後で Oracle データベースをパブリッシャーとして構成するときにこの情報の入力が要求されるため、どちらもメモしておいてください。 スキーマはレプリケーションに必要なオブジェクトでのみ使用し、このスキーマではパブリッシュするテーブルを作成しないでください。  
  
### 手動によるユーザー スキーマの作成  
 レプリケーション管理ユーザー スキーマを手動で作成する場合は、スキーマに次の権限を直接またはデータベース ロールを通じて許可する必要があります。  
  
-   CREATE PUBLIC SYNONYM および DROP PUBLIC SYNONYM  
  
-   CREATE PROCEDURE  
  
-   CREATE SEQUENCE  
  
-   CREATE SESSION  
  
 また、次の権限を、(ロールを通じてではなく) 直接ユーザーに許可する必要もあります。  
  
-   CREATE ANY TRIGGER。 これは、スナップショット レプリケーションとトランザクション レプリケーションの両方の場合にのみ必要です。  
  
-   CREATE TABLE  
  
-   CREATE VIEW  
  
## SQL Server ディストリビューターへの Oracle クライアント ネットワーク ソフトウェアのインストールと構成  
 Oracle クライアント ネットワーク ソフトウェアおよび Oracle OLE DB プロバイダーを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターにインストールして構成し、ディストリビューターが Oracle パブリッシャーと接続できるようにします。 ソフトウェアをインストールしたら、ソフトウェアがインストールされているフォルダーに適切な権限を設定し、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスを停止して再起動してからすべての設定が更新されているかどうかを確認します (権限については、この後の「ディレクトリ権限の設定」を参照してください)。  
  
> [!NOTE]  
>  Oracle クライアント ネットワーク ソフトウェアは、最新バージョンであることが必要です。 Oracle では、最新バージョンのクライアント ソフトウェアをインストールすることを推奨しています。 このため、データベース ソフトウェアよりもクライアント ソフトウェアの方が新しいバージョンであることがよくあります。  
  
 クライアント ネットワーク ソフトウェアを最も簡単にインストールおよび構成するには、Oracle クライアント ディスクの Oracle Universal Installer と Net Configuration Assistant を使用します。  
  
 Oracle Universal Installer で、次の情報を指定します。  
  
|情報|説明|  
|-----------------|-----------------|  
|Oracle ホーム|Oracle ソフトウェアのインストール ディレクトリのパスです。 既定値 (C:\oracle\ora90 など) をそのまま使用するか、別のパスを入力します。 Oracle ホームの詳細については、このトピックの「Oracle ホームに関する注意点」を参照してください。|  
|Oracle ホーム名|Oracle ホーム パスの別名|  
|インストールの種類|Oracle 10 g では、選択、 **管理者** インストール オプションです。|  
  
 Oracle Universal Installer が完了したら、Net Configuration Assistant を使用してネットワーク接続を構成します。 ネットワーク接続を構成するには、4 つの情報を指定する必要があります。 Oracle データベース管理者は、データベースとリスナーをセットアップするときにネットワークを構成しています。この情報が不明な場合は、管理者に問い合わせてください。 以下の操作を行う必要があります。  
  
|操作|説明|  
|------------|-----------------|  
|データベースを識別する|データベースは 2 とおりの方法で識別できます。 1 つ目は、SID (Oracle System Identifier) を使用する方法で、すべての Oracle リリースで使用できます。 2 つ目は、サービス名を使用する方法で、Oracle リリース 8.0 以降で使用できます。 どちらの方法も、データベースの作成時に構成される値を使用します。データベースのリスナーの構成時に管理者が使用したものと同じ命名方法を、クライアント ネットワーク構成でも使用することが重要です。|  
|データベースのネットワークの別名を識別する|Oracle データベースへのアクセスに使用するネットワークの別名を指定する必要があります。 Oracle データベースを、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターでパブリッシャーとして識別するときに、この別名を指定します。 ネットワークの別名とは、基本的にはデータベースの作成時に構成されたリモート SID またはサービス名へのポインターです。ネットワークの別名は、各種の Oracle リリースや製品では、ネット サービス名や TNS 別名など、複数の名前で呼ばれています。 SQL*Plus では、ログイン時に "ホスト文字列" パラメーターとしてこの別名の入力画面が表示されます。|  
|ネットワーク プロトコルを選択する|サポート対象とする適切なプロトコルを選択します。 ほとんどのアプリケーションでは TCP を使用します。|  
|データベース リスナーを識別するホスト情報を指定する|ホストは、Oracle リスナーを実行中のコンピューターの名前または DNS 別名で、通常はデータベースが存在しているコンピューターです。 プロトコルによっては、追加情報を指定する必要があります。 たとえば、TCP を選択した場合は、リスナーが対象データベースへの接続要求を受信待ちしているポートを指定する必要があります。 既定の TCP 構成ではポート 1521 を使用します。|  
  
### ディレクトリ権限の設定  
 ディストリビューター上の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスが実行されるアカウントには、Oracle クライアント ネットワーク ソフトウェアがインストールされているディレクトリ (およびすべてのサブディレクトリ) に対する読み取り権限と実行権限を付与する必要があります。  
  
### SQL Server ディストリビューターと Oracle パブリッシャー間の接続のテスト  
 Net Configuration Assistant の終了間際に、Oracle パブリッシャーへの接続をテストするオプションを選択できます。 接続をテストする前に、Oracle データベース インスタンスがオンラインで、Oracle リスナーが実行中であることを確認してください。 テストが成功しなかった場合、接続しようとするデータベースを担当する Oracle DBA に連絡してください。  
  
 Oracle パブリッシャーへの接続に成功したら、作成したレプリケーション管理ユーザー スキーマに関連付けられたアカウントとパスワードを使用してデータベースにログインします。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスが使用しているアカウントと同じ Windows アカウントで実行している場合は、次の操作を行う必要があります。  
  
1.  クリックして **開始**, 、順にクリック **実行**します。  
  
2.  型 `cmd` ] をクリック **OK**します。  
  
3.  コマンド プロンプトで、次のように入力します。  
  
     `sqlplus <UserSchemaLogin>/<UserSchemaPassword>@<NetServiceName>`  
  
     例: `sqlplus replication/$tr0ngPasswerd@Oracle90Server`  
  
4.  ネットワーク構成が正常に行われていれば、ログインは成功し、`SQL` プロンプトが表示されます。  
  
5.  Oracle データベースへの接続に問題が発生した場合は、セクションを参照してください"、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターが Oracle データベース インスタンスに接続できません"で [Oracle パブリッシャーのトラブルシューティング](../../../relational-databases/replication/non-sql/troubleshooting-oracle-publishers.md)します。  
  
### Oracle ホームに関する注意点  
 Oracle では、アプリケーション バイナリをサイド バイ サイド インストールできますが、ある時点でレプリケーションが使用できるバイナリ セットは 1 つだけです。 各バイナリ セットは Oracle ホームに関連付けられ、バイナリはディレクトリ %ORACLE_HOME%\bin に格納されます。 レプリケーションが Oracle パブリッシャーに接続するときに、正しいバイナリ セット (具体的には最新バージョンのクライアント ネットワーク ソフトウェア) が使用されるようにしてください。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスおよび [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント サービスで使用されるアカウントを使ってディストリビューターにログインし、適切な環境変数を設定します。 %ORACLE_HOME% 変数は、クライアント ネットワーク ソフトウェアをインストールしたときに指定したインストール ポイントを参照するように設定する必要があります。 %PATH% には、最初に検出される Oracle エントリとして %ORACLE_HOME% \bin ディレクトリを含める必要があります。 環境変数の設定の詳細については、Windows のマニュアルを参照してください。  
  
## SQL Server ディストリビューターでの Oracle データベースのパブリッシャーとしての構成  
 Oracle パブリッシャーは常にリモート ディストリビューターを使用するため、Oracle パブリッシャーのディストリビューターとして機能するように [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスを構成する必要があります。1 つの Oracle パブリッシャーは 1 つのディストリビューターのみ使用しますが、1 つのディストリビューターは複数の Oracle パブリッシャーに対応できます。 ディストリビューターを構成したら、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターで、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、Transact-SQL、レプリケーション管理オブジェクト (RMO) を通じて Oracle データベース インスタンスをパブリッシャーとして識別します。 ディストリビューターの構成の詳細については、次を参照してください。 [ディストリビューションの構成](../../../relational-databases/replication/configure-distribution.md)します。  
  
> [!NOTE]  
>  Oracle パブリッシャーの名前を、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターと同じ名前、または同じディストリビューターを使用する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] パブリッシャーと同じ名前にすることはできません。  
  
 Oracle データベースをパブリッシャーとして識別する場合は、Oracle パブリッシング オプションの [Complete] または [Oracle (ゲートウェイ)] を選択する必要があります。 パブリッシャーを識別した後は、パブリッシャーをいったん削除して再構成しない限り、このオプションは変更できません。 [Complete] オプションでは、スナップショット パブリケーションとトランザクション パブリケーションに、Oracle パブリッシングでサポートされるすべての機能セットが提供されます。 [Oracle (ゲートウェイ)] オプションでは、システム間のゲートウェイとしてレプリケーションが機能する場合にパフォーマンスを向上させるための最適化が行われます。  
  
 Oracle パブリッシャーを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターで識別した後、レプリケーションによって Oracle データベースの TNS サービス名と同じ名前のリンク サーバーが作成されます。 このリンク サーバーはレプリケーションでのみ使用できます。 リンク サーバー接続を介して、Oracle パブリッシャーに接続する場合は、別の TNS サービス名を作成しを呼び出すときにこの名前を使用して [sp_addlinkedserver & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)です。  
  
 Oracle パブリッシャーを構成してパブリケーションを作成を参照してください。 [Oracle データベースからパブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md)です。  
  
## 参照  
 [Oracle パブリッシャーの管理上の注意点](../../../relational-databases/replication/non-sql/administrative-considerations-for-oracle-publishers.md)   
 [Oracle パブリッシャーのデータ型マッピング](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [Oracle パブリッシングの用語](../../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Oracle パブリッシングの概要](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  