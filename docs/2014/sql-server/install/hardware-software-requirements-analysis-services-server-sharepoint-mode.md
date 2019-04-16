---
title: SharePoint モード (SQL Server 2014) での Analysis Services サーバーのハードウェアおよびソフトウェア |Microsoft Docs
ms.prod: sql-server-2014
ms.technology:
- database-engine
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.topic: conceptual
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: 95004fde44989d130664d73b044f833cd94f8d88
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2019
ms.locfileid: "59581896"
---
# <a name="hardware-and-software-requirements-for-analysis-services-server-in-sharepoint-mode-sql-server-2014"></a>SharePoint モードの Analysis Services サーバーのハードウェアとソフトウェアの要件 (SQL Server 2014)

[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] は、SharePoint 2010 と SharePoint 2013 の両方をサポートしています。 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 は SharePoint ファームの外部で実行されますが、SharePoint サーバー上にインストールすることもできます。 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010 は、SharePoint 2010 ファーム内のアプリケーション サーバー上で動作し、SharePoint の機能とインフラストラクチャを使用してサーバー操作をサポートします。 SharePoint のいずれかのバージョンの [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] をインストールするには、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インストール ウィザードを使用します。 インストール後に、次の手順を完了します。  
  
- SharePoint のバージョンに応じた、適切なバージョンの [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 構成ツールを実行します。  
  
- SharePoint 2013 では、インストール、[インストールまたは PowerPivot を SharePoint アドインのアンインストール&#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)します。  

##  <a name="bkmk_sqleditions"></a> SQL Server エディションの要件  
 ビジネス インテリジェンス機能は、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のすべてのエディションで利用できるわけではありません。 詳細については、次を参照してください。[機能は、SQL Server 2014 の各エディションでサポートされている](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)と[エディションと SQL Server 2014 のコンポーネントの](../editions-and-components-of-sql-server-2016.md)します。  
  
 現在のリリース ノートをご覧[Microsoft SQL Server 2014 リリース ノート](https://go.microsoft.com/fwlink/?LinkID=296445)します。  
  

  
##  <a name="bkmk_sqllicense"></a> SQL Server のライセンス  
 SQL Server のライセンスの詳細については、以下を参照してください。  
  
-   [SQL Server 2014 ライセンス データシート](https://download.microsoft.com/download/6/6/F/66FF3259-1466-4BBA-A505-2E3DA5B2B1FA/SQL_Server_2014_Licensing_Datasheet.pdf)(https://download.microsoft.com/download/6/6/F/66FF3259-1466-4BBA-A505-2E3DA5B2B1FA/SQL_Server_2014_Licensing_Datasheet.pdf)します。  
  
-   [購入方法。SQL Server のライセンス モデルでサポート](https://www.microsoft.com/licensing/product-licensing/sql-server-2014?activetab=sql-server-2014-pivot%3aprimaryr2)(https://www.microsoft.com/licensing/product-licensing/sql-server-2014?activetab=sql-server-2014-pivot%3aprimaryr2)します。  
  
##  <a name="bkmk_ssas__sharepoint_2013"></a> SharePoint 2013 にインストールされている analysis Services  
 Analysis Services サーバーだけを SharePoint モードでサーバーにインストールする場合、最小システム要件は、SharePoint サーバーの要件ではなく [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] に基づきます。  
  
 [SQL Server 2014 のインストールに必要なハードウェアおよびソフトウェア](hardware-and-software-requirements-for-installing-sql-server.md)  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint は、RAM のしきい値と処理能力が高い新世代のビジネス サーバー上で最適に動作します。 メモリへの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データの格納には大量の RAM が使用されます。 RAM は構造の変化に対応できる機能をサポートしています。 追加のプロセッサでは、生の未集計データの実行時間の長いスキャンをサポートします。 このデータの構造は、ユーザーが Excel クライアントやフロントエンド インターフェイスを使用して開始したデータ分析に応じて動的に変化します。  
  
> [!TIP]  
>  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint では、L2 キャッシュと L3 キャッシュを使用します。 パフォーマンスを向上させるには、大容量の L2 および L3 キャッシュが搭載されたプロセッサを使用することを検討してください。  
  
 次の表では、SharePoint ファームの一部ではないスタンドアロン [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] サーバーの最小ハードウェア構成と推奨構成を示しています。  
  
|コンポーネント|最小|推奨|  
|---------------|-------------|-----------------|  
|プロセッサ|64 ビット デュアルコア プロセッサ、3 GHz|16 コア|  
|RAM|8 GB の RAM|64 GB の RAM|  
|ストレージ|80 GB のストレージ|80 GB 以上|  
  
 Analysis Services サーバーを SharePoint モードで SharePoint ファームのサーバーにインストールする場合は、以下のリンクで、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] サーバーと SharePoint サーバー両方の最小システム要件を確認してください。  
  
-   [SQL Server 2014 のインストールに必要なハードウェアおよびソフトウェア](hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [For SharePoint 2013 のハードウェアおよびソフトウェア要件](https://technet.microsoft.com/library/cc262485\(office.15\).aspx)します。  
  
 SharePoint 2013 のハードウェアおよびソフトウェアの標準の推奨構成は、ワークグループまたはチーム向けの Web ベースのドキュメント管理ソリューション用の構成です。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 処理ではデータが集中的に使用されますが、ワークロード全体の数が少ない場合 (たとえば、ユーザー数またはブック数が 100 件未満の場合) は、標準の推奨設定で十分です。 大規模な [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] の配置を行う場合は、さらに高い処理能力が必要です。  
  
##  <a name="bkmk_ssas__sharepoint_2010"></a> SharePoint 2010 サーバーにインストールされている analysis Services  
 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010 は、SharePoint 2010 ファーム内のアプリケーション サーバー上で動作し、SharePoint の機能とインフラストラクチャを使用してサーバー操作をサポートします。 次の表は、 SharePoint 2010 の配置に関連する要件をまとめたものです。  
  
|コンポーネント|要件|  
|---------------|-----------------|  
|SharePoint バージョン|同じサーバー ファーム内で Excel Services、Secure Store Service、および Claims to Windows Token Service が構成された SharePoint 2010 Enterprise。<br /><br /> SharePoint は、SharePoint セットアップでサーバー ファーム オプションを使用してインストールされている必要があります (SharePoint のスタンドアロン インストール オプションはサポートされていません)。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] には、管理アクセスおよびデータ アクセスをサポートするサーバー ファーム インフラストラクチャが必要です。 スタンドアロン インストールではこれらのサービスは提供されません。<br /><br /> [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバーのインストールでは、Windows 7 または Windows Vista 上で動作する Developer Edition はサポートされません。|  
|サービス パック|SharePoint Server 2010 Service Pack 1 (SP1) が必要です。<br /><br /> SharePoint 2010 Service Pack 1 が必要な[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]機能します。<br /><br /> 以前のバージョンの [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] から [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] にアップグレードする場合は、SharePoint 2010 の 2010 年 8 月の累積的な更新プログラム、またはそれ以降の更新プログラムが必要です。 2010 年 8 月の累積的な更新プログラム、またはそれ以降の更新プログラムは、SharePoint Service Pack 1 のインストール後にインストールする必要があります。 新しいインストール[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]累積更新プログラムは必要ありません。 詳細については、次を参照してください。 [2010 for SharePoint の累積更新プログラムがリリースされた月](http://blogs.technet.com/b/stefan_gossner/archive/2010/09/02/august-2010-cumulative-update-for-sharepoint-has-been-released.aspx)します。|  
|SharePoint web アプリケーション|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint 2010 は、クラシック モード認証用に構成された SharePoint Web アプリケーションのみをサポートします。 既存のファームに [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint を追加する場合は、使用する予定の Web アプリケーションがクラシック モード認証用に構成されていることを確認してください。 手順については、セクションを参照してください。 認証モードを確認する方法の"Web アプリケーションを確認してくださいではクラシック モード認証" [SharePoint に PowerPivot ソリューションの配置](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)します。|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバー側のデータ更新に必要なデータ プロバイダー|サーバー側のデータの更新を行うと、最初にデータをインポートするために使用したのと同じデータ取得手順が繰り返されます。 これは、クライアント ワークステーションでデータのインポートに使用されるデータ プロバイダーが、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint サーバーにも存在する必要があることを示します。<br /><br /> また、SharePoint サーバー上のデータ フィードを使用するには、ADO.NET Data Services が必要です。 SharePoint の必須コンポーネントのインストーラー プログラムでは、このコンポーネントはインストールされません。 次のソフトウェアを手動でインストールする必要があります。<br /><br /> ADO.NET Data Services 3.5 SP1 ランタイム アセンブリ。このアセンブリは、SharePoint リストをデータ フィードとしてエクスポートするために使用します。 使用しているオペレーティング システムに対応するバージョンをダウンロードしてインストールしてください。<br /><br /> Windows Server 2008 r2 を使用して、 [.NET Framework 3.5 SP1 を Windows 7 および windows Server 2008 R2 用 ADO.NET Data Services 更新プログラム (https://go.microsoft.com/fwlink/?LinkId=182557)](https://go.microsoft.com/fwlink/?LinkId=182557)します。 Windows Server 2008 R2 **SP1**更新されたプロバイダーが既に含まれています。<br /><br /> Windows Server 2008 を使用して、 [.NET Framework 3.5 SP1 を Windows 2000、Windows Server 2003、Windows XP、Windows Vista および Windows Server 2008 の ADO.NET Data Services 更新プログラム (https://go.microsoft.com/fwlink/?LinkId=158125)](https://www.microsoft.com/download/details.aspx?id=22734)します。|  
  
 [特定のハードウェアとソフトウェア要件 (SharePoint 2010) (https://go.microsoft.com/fwlink/?LinkId=169734)](https://go.microsoft.com/fwlink/?LinkId=169734)  
  
## <a name="additional-information"></a>追加情報  

SharePoint の変更点については、次を参照してください。 [SharePoint 2010 から SharePoint 2013 への変更](https://technet.microsoft.com/library/ff607742\(office.15\).aspx)(https://technet.microsoft.com/library/ff607742(office.15).aspx)します。