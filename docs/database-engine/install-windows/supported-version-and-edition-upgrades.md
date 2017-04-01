---
title: "サポートされているバージョンとエディションのアップグレード | Microsoft Docs"
ms.custom: ""
ms.date: "08/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コンポーネント [SQL Server]、既存のインストールへの追加"
  - "バージョン [SQL Server]、アップグレード"
  - "SQL Server のアップグレード、サポートされているアップグレード"
  - "言語間サポート"
ms.assetid: 702359c4-6ca9-42a8-860c-a95a802898a1
caps.latest.revision: 148
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 147
---
# サポートされているバージョンとエディションのアップグレード
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、および [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] からアップグレードできます。 このトピックでは、これらの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンからのサポートされているアップグレード パスと、サポートされている [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] へのエディションのアップグレードを示します。  
  
## アップグレード前のチェック リスト  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のいずれかのエディションから別のエディションへアップグレードする前に、現在使用している機能が移動先のエディションでサポートされているかどうかを確認します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をアップグレードする前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの Windows 認証を有効にし、既定の構成 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのサービス アカウントが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sysadmin グループのメンバーであること) を確認してください。  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードするには、サポート対象のオペレーティング システムを実行している必要があります。 詳細については、「[SQL Server 2016 のインストールに必要なハードウェアおよびソフトウェア](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)」を参照してください。  
  
-   再起動を保留している場合はアップグレードがブロックされます。  
  
-   Windows インストーラー サービスが実行されていない場合は、アップグレードがブロックされます。  
  
## サポートされていないシナリオ  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の複数バージョンにまたがるインスタンスの使用はサポートされていません。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントのバージョン番号は [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインスタンス内で同一であることが必要です。  
  
-   SQL Server 2016 は、64 ビット プラットフォームでのみ利用できます。 クロスプラットフォームのアップグレードはサポートされていません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 32 ビット インスタンスをネイティブ 64 ビットにアップグレードすることはできません。 ただし、データベースがレプリケーションでパブリッシュされていない場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 32 ビット インスタンスのデータベースをバックアップまたはデタッチしてから、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新しいインスタンス (64 ビット) に復元またはアタッチすることができます。 master、msdb、および model の各システム データベースにある、すべてのログインとその他のユーザー オブジェクトを再作成する必要があります。  
  
-   既存の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのアップグレード中は、新しい機能を追加できません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードした後、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のセットアップを使用して機能を追加できます。 詳細については、「[SQL Server 2016 のインスタンスへの機能の追加 &#40;セットアップ&#41;](../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md)」を参照してください。  
 
-   フェールオーバー クラスターは、WOW モードでサポートされていません。  
  
-   以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の Evaluation Edition からのアップグレードはサポートされていません。  
  
## 以前のバージョンから [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 
SQL Server 2016 では、次のバージョンの SQL Server からのアップグレードがサポートされます。
 
- SQL Server 2008 SP3 以降
- SQL Server 2008 R2 SP2 以降
- SQL Server 2012 SP2 以降
- SQL Server 2014 以降 
 

  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] でデータベースをアップグレードするには、[2005 のサポート](#SupportFor2005)を参照してください。  
  
 次の表に示すのは、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] への、サポートされるアップグレード シナリオです。  
  
|アップグレード元|サポートされているアップグレード パス|  
|------------------|----------------------------|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Enterprise|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Developer|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Standard|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Small Business|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Web|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Workgroup|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP3 Express |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Datacenter|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Enterprise|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Developer|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Small Business|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Standard|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Web|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Workgroup|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP2 Express |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 Enterprise|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 Developer|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 開発者 <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 Standard|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 Web|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 Express |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express <br/> <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 Business Intelligence|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 Evaluation|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Evaluation <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 開発者|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 開発者|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 開発者 <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 開発者|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Evaluation|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Evaluation <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 開発者|  
|[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] リリース候補 * |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise |  
|[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 開発者 |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise | 

 \* Microsoft では、特に Technology Adoption Program (TAP) に参加したお客様向けに、リリース候補版ソフトウェアからのアップグレードをサポートしています。 

   
###  <a name="SupportFor2005"></a> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] サポート対象 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
 ここでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] に対する [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] のサポートについて説明します。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、次の作業を実行できます。  
  
-   データベース エンジンの [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] インスタンスに、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] データベース (mdf/ldf ファイル) をアタッチします。  
  
-   バックアップからデータベース エンジンの [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] インスタンスに [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] データベースを復元します。  
  
-   [!INCLUDE[ssASversion2005](../../includes/ssasversion2005-md.md)] キューブをバックアップし、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] に復元します。  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] データベースを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードすると、そのデータベースの互換性レベルは 90 から 100 に変更されます  ([!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のデータベース互換性レベルの有効な値は 100、110、120、および 130 です)。[ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20Compatibility%20Level%20\(Transact-SQL\).md) は、互換性レベルの変更が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アプリケーションに与える影響について説明します。  
  
 上記の一覧で説明されていないどのシナリオもサポートされていませんが、以下のシナリオに限定されるものではありません。  
  
-   同じコンピューターへの [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] と [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の (サイド バイ サイド) インストール。  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] インスタンスに参加するレプリケーション トポロジのメンバーとして [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インスタンスを使用する。  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インスタンスと [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] インスタンスの間でのデータベース ミラーリングの構成。  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インスタンスと [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] インスタンスの間でのログ配布によるトランザクション ログのバックアップ。  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インスタンスと [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] インスタンスの間でのリンク サーバーの構成。  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Management Studio からの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インスタンスの管理。  
  
-   [!INCLUDE[ssASversion2005](../../includes/ssasversion2005-md.md)] Management Studio 内での [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] キューブのアタッチ。  
  
-   [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] Management Studio から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] への接続  
  
-   [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] Management Studio からの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] サービスの管理。  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] のサード パーティのカスタム Integration Services コンポーネントに対するサポート (実行とアップグレードなど)。  
  
## [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] エディションのアップグレード  
 次の表に示すのは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] でサポートされるエディションのアップグレード シナリオです。  
  
 エディションのアップグレードを実行する手順については、「[SQL Server 2016 の別のエディションへのアップグレード &#40;セットアップ&#41;](../../database-engine/install-windows/upgrade-to-a-different-edition-of-sql-server-2016-setup.md)」を参照してください。  
  
|アップグレード元|アップグレード先|  
|------------------|----------------|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (Server+CAL および Core)**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise |  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Evaluation Enterprise**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (Server+CAL または Core ライセンス) <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> Evaluation (無償エディション) からいずれかの有償エディションへのアップグレードは、スタンドアロン インストールではサポートされていますが、クラスター化インストールではサポートされていません。|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (Server+CAL または Core ライセンス)|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (Server+CAL または Core ライセンス) <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (Server+CAL または Core ライセンス) <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express*|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (Server+CAL または Core ライセンス) <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 開発者 <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web|  
  
 さらに、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (Server+CAL ライセンス) と [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (Core License) の間でエディションのアップグレードも実行できます。  
  
|エディションのアップグレード元|エディションのアップグレード先|  
|--------------------------|------------------------|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (Server+CAL ライセンス)**|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (Core ライセンス)|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (Core ライセンス)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (Server+CAL ライセンス)|  
  
 \* [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express with Tools および [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express with Advanced Services についても同様です。  
  
 ** [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] フェールオーバー クラスターのエディションの変更は制限されています。 次のシナリオは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] フェールオーバー クラスターではサポートされていません。  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer、Standard、または Evaluation への変更  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard または Evaluation への変更  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Evaluation への変更  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Evaluation から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard への変更  
  
## 参照  
 [SQL Server 2016 の各エディションでサポートされる機能](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)   
 [SQL Server 2016 のインストールに必要なハードウェアおよびソフトウェア](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)   
 [SQL Server 2016 へのアップグレード](../../database-engine/install-windows/upgrade-to-sql-server-2016.md)  
  
  