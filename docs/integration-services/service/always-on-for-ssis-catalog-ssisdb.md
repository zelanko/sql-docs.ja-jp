---
title: "Always On for SSIS Catalog (SSISDB) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.ssms.alwayson.f1"
ms.assetid: 7f089455-35ee-4c13-884e-9254b685d07d
caps.latest.revision: 17
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 16
---
# Always On for SSIS Catalog (SSISDB)
  Always On 可用性グループ機能は、データベース ミラーリングに代わる、高可用性と災害復旧のためのエンタープライズ レベルのソリューションです。 可用性グループは、可用性データベースというひとまとまりでフェールオーバーされる個別のユーザー データベースのセットのためのフェールオーバー環境をサポートします。 詳細については、「 [AlwaysOn 可用性グループ (SQL Server)](https://msdn.microsoft.com/library/hh510230.aspx)」を参照してください。  
  
 SSIS カタログ (SSISDB) とそのコンテンツ (プロジェクト、パッケージ、実行ログなど) の高可用性を実現するには、(他のユーザー データベースと同様に) SSISDB データベースを Always On 可用性グループに追加できます。 フェールオーバーが発生すると、セカンダリ ノードのいずれかが自動的に新しいプライマリ ノードになります。  
 
 > [!IMPORTANT]  フェールオーバーが発生した場合、実行中のパッケージの再起動や再開は行われません。 
 
 **このトピックの内容:**  
  
1.  [前提条件](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#prereq)  
  
2.  [Always On の SSIS サポートを構成する](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Firsttime)  
  
3.  [可用性グループの SSISDB をアップグレードする](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Upgrade)  
  
##  <a name="a-nameprereqa-prerequisites"></a><a name="prereq"></a> の前提条件  
 次の前提条件手順を実行してから、SSISDB データベースの Always On サポートを有効にする必要があります。  
  
1.  Windows フェールオーバー クラスターを設定します。 手順については、「 [Installing the Failover Cluster Feature and Tools for Windows Server 2012 (Windows Server 2012 のフェールオーバー クラスター機能とツールのインストール)](http://blogs.msdn.com/b/clustering/archive/2012/04/06/10291601.aspx) 」のブログ投稿を参照してください。 すべてのクラスター ノードに機能とツールをインストールする必要があります。  
  
2.  クラスターの各ノードに SQL Server 2016 with Integration Services (SSIS) 機能をインストールします。  
  
3.  各 SQL Server インスタンスで Always On 機能を有効にします。 詳細については、「 [Always On 可用性グループの有効化と無効化 (SQL Server)](https://msdn.microsoft.com/library/ff878259.aspx) 」を参照してください。  
  
##  <a name="a-namefirsttimea-configure-ssis-support-for-always-on"></a><a name="Firsttime"></a> Always On の SSIS サポートを構成する  
  
-   [手順 1: Integration Services カタログを作成する](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Step1)  
  
-   [手順 2: SSISDB を Always On 可用性グループに追加する](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Step2)  
  
-   [手順 3: Always On の SSIS サポートを有効にする](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Step3)  
  
> [!IMPORTANT]  
>  -   可用性グループの **プライマリ ノード** で、次の手順を実行する必要があります。  
> -   SSISDB を Always On グループに追加した後に、 **Always On の SSIS サポート** を有効にする必要があります。  
  
###  <a name="a-namestep1a-step-1-create-integration-services-catalog"></a><a name="Step1"></a> 手順 1: Integration Services カタログを作成する  
  
1.  **SQL Server Management Studio** を起動し、SSISDB の Always On 高可用性グループの **プライマリ ノード** として設定するクラスターの SQL Server インスタンスに接続します。  
  
2.  オブジェクト エクスプローラーで、サーバー ノードを展開します。次に、 **[Integration Services カタログ]** ノードを右クリックし、 **[カタログの作成]**をクリックします。  
  
3.  **[CLR 統合を有効にする]**をクリックします。 カタログは CLR ストアド プロシージャを使用します。  
  
4.  SSIS サーバー インスタンスを再起動するたびに **catalog.startup** ストアド プロシージャが実行されるようにするには、 [[SQL Server のスタートアップ時に Integration Services ストアド プロシージャを自動実行できるようにする]](https://msdn.microsoft.com/library/hh230984.aspx) をクリックします。 このストアド プロシージャは、SSISDB カタログに対する操作の状態のメンテナンスを実行します。 SSIS サーバー インスタンスがダウンした場合に、実行されていたパッケージの状態を修正します。  
  
5.  **パスワード**を入力し、 **[OK]**をクリックします。 カタログ データを暗号化するために使用されるデータベース マスター キーがパスワードで保護されます。 パスワードは安全な場所に保管してください。 データベース マスター キーをバックアップすることもお勧めします。 詳細については、「 [データベース マスター キーのバックアップ](https://msdn.microsoft.com/library/aa337546.aspx)」を参照してください。  
  
###  <a name="a-namestep2a-step-2-add-ssisdb-to-an-always-on-availability-group"></a><a name="Step2"></a> 手順 2: SSISDB を Always On 可用性グループに追加する  
 SSISDB データベースを Always On 可用性グループに追加する手順は、他のユーザー データベースを可用性グループに追加する場合とほぼ同じです。 「 [可用性グループ ウィザードの使用](https://msdn.microsoft.com/library/hh403415.aspx)」を参照してください。  
  
 **新しい可用性グループ** ウィザードの **[データベースの選択]** ページで SSIS カタログを作成するときに指定したパスワードを入力する必要があります。  
  
 ![New Availability Group](../../integration-services/service/media/ssis-newavailabilitygroup.png "New Availability Group")  
  
###  <a name="a-namestep3a-step-3-enable-ssis-support-for-always-on"></a><a name="Step3"></a> 手順 3: Always On の SSIS サポートを有効にする  
 Integration Service カタログを作成した後に、 **[Integration Service カタログ]** ノードを右クリックし、 **[AlwaysOn サポートを有効にする]**をクリックします。 次の **[AlwaysOn のサポートを有効にする]** ダイアログ ボックスが表示されます。 このメニュー項目が無効な場合、すべての前提条件がインストールされていることを確認してから、 **[更新]**をクリックします。  
  
 ![Enable Support for AlwaysOn](../../integration-services/service/media/ssis-enablesupportforalwayson.png "Enable Support for AlwaysOn")  
  
> [!WARNING]  
>  SSISDB データベースの自動フェールオーバーをサポートするには、Always On のSSIS のサポートを有効にする必要があります。  
  
 AlwaysOn 可用性グループから新しく追加したセカンダリ レプリカが一覧に表示されます。 SSIS サーバー インスタンスを再起動するたびに **[接続]** ボタンをクリックして、認証資格情報を入力してレプリカに接続します。 SSIS Always On のサポートを有効にするには、ユーザー アカウントは、各レプリカの sysadmin グループのメンバーである必要があります。 各レプリカに正常に接続できたら、 **[OK]** をクリックして、Always On の SSIS のサポートを有効にします。  
  
##  <a name="a-nameupgradea-upgrading-ssisdb-in-an-availability-group"></a><a name="Upgrade"></a> 可用性グループの SSISDB をアップグレードする  
 以前のバージョンから SQL Server をアップグレードし、SSISDB が Always On 可用性グループに含まれる場合、"Always On 可用性グループの SSISDB チェック" 規則でアップグレードがブロックされることがあります。 このブロックが発生するのは、可用性データベースがマルチユーザー データベースである必要があるにもかかわらず、アップグレードがシングル ユーザー モードで実行されたためです。 そのため、アップグレードまたは修正プログラムの適用中には、SSISDB を含むすべての可用性データベースがオフラインになり、アップグレードまたは修正プログラムの適用が行われません。 アップグレードを続行するには、まず可用性グループから SSISDB を削除してから、各ノードのアップグレードまたは修正プログラムの適用を行ってから、SSISDB を可用性グループに追加する必要があります。  
  
 "Always On 可用性グループ内の SSISDB の確認" の規則でブロックされる場合、次の手順に従って SQL Server をアップグレードする必要があります。  
  
1.  可用性グループから SSISDB を削除します。 詳細については、「[可用性グループからのセカンダリ データベースの削除 (SQL Server)](../../database-engine/availability-groups/windows/remove-a-secondary-database-from-an-availability-group-sql-server.md)」および「[可用性グループからのプライマリ データベースの削除 (SQL Server)](../../database-engine/availability-groups/windows/remove-a-primary-database-from-an-availability-group-sql-server.md)」を参照してください。  
  
2.  アップグレード ウィザードで **[再実行]** をクリックします。 "Always On 可用性グループ内の SSISDB の確認" 規則に合格します。  
  
3.  **[次へ]** をクリックしてアップグレードを続行します。  
  
4.  すべてのノードをアップグレードしたら、SSISDB データベースを Always On 可用性グループに追加します。 詳細については、「[可用性グループへのデータベースの追加 (SQL Server)](../../database-engine/availability-groups/windows/add-a-database-to-an-availability-group-sql-server.md)」を参照してください。  
  
 SQL Server のアップグレード時にブロックされず、SSISDB が Always On 可用性グループに属している場合、SQL Server データベース エンジンをアップグレードした後に、別に SSISDB をアップグレードする必要があります。 次の手順で、SSIS アップグレード ウィザードを使用して SSISDB をアップグレードします。  
  
1.  可用性グループから SSISDB データベースを削除するか、SSISDB が可用性グループで唯一のデータベースの場合は可用性グループを削除します。 このタスクを実行するには、可用性グループの **プライマリ ノード** で **SQL Server Management Studio** を起動する必要があります。  
  
2.  すべての **レプリカ ノード**から SSISDB データベースを削除します。  
  
3.  **プライマリ ノード**の SSISDB データベースをアップグレードします。 SQL Server Management Studio の**オブジェクト エクスプローラー** で、 **[Integration Service カタログ]**を展開し、 **[SSISDB]**を右クリックし、 **[データベース アップグレード]**を選択します。 **SSISDB アップグレード ウィザード** の指示に従ってデータベースをアップグレードします。 **SSIDB アップグレード ウィザード** は、 **プライマリ ノード**のローカルで起動する必要があります。  
  
4.  SSISDB を可用性グループに追加する手順については、「 [手順 2: SSISDB を Always On 可用性グループに追加する](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Step2) 」を参照してください。  
  
5.  「 [手順 3: Always On の SSIS サポートを有効にする](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Step3)」の指示に従います。  
  
  