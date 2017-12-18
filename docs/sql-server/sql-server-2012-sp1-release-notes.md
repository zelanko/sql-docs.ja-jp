---
title: "SQL Server 2012 SP1 リリース ノート | Microsoft Docs"
ms.prod: sql-server
ms.prod_service: sql-non-specified
ms.service: server-general
ms.component: 
ms.technology: server-general
ms.custom: 
ms.date: 01/31/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72171357-28de-4edd-bdfd-194f97225a6f
caps.latest.revision: "49"
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 47e51354f3a7239635cae40bc3ba3d99bb6be35a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sql-server-2012-sp1-release-notes"></a>SQL Server 2012 SP1 リリース ノート
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)] このリリース ノートでは、[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 1 のインストールやトラブルシューティングを行う前に知っておく必要がある、既知の問題について説明しています。 このリリース ノートは、オンラインのみで入手でき、インストール メディアには含まれていません。また、定期的に更新されます。  
  
## <a name="bkmk_top"></a>目次  
[1.0 インストールの準備](#bmk_Install)  
  
[2.0 Analysis Services と PowerPivot](#bkmk_AS)  
  
[3.0 Reporting Services](#bkmk_RS)  
  
[4.0 Data Quality Services](#bkmk_DQS)  
  
[5.0 SQL Server Express](#bkmk_Express)  
  
[6.0 Change Data Capture Service for Oracle by Attunity と Change Data Capture Designer for Oracle by Attunity](#bkmk_CDC)  
  
[7.0 SQL Server Data-Tier Application Framework (DACFx)](#DACFx)  
  
[8.0 この Service Pack で修正された既知の問題](#bkmk_known_issues_fixed)  
  
## <a name="bmk_Install"></a>1.0 インストールの準備  
SQL Server 2012 SP1 をインストールする前に、次のことを考慮してください。  
  
### <a name="11-reinstalling-an-instance-of-sql-server-failover-custer-fails-if-you-use-the-same-ip-address"></a>1.1 同じ IP アドレスを使用すると SQL Server フェールオーバー クラスターのインスタンスの再インストールに失敗する  
**問題点:** SQL Server フェールオーバー クラスター インスタンスのインストール中に正しくない IP アドレスを指定すると、インストールが失敗します。 失敗したインスタンスをアンインストールした後に、同じインスタンス名と適切な IP アドレスを使用して SQL Server フェールオーバー クラスター インスタンスを再インストールしようとすると、インストールは失敗します。 このエラーは、前のインストールによって残されたリソース グループが重複するため発生します。  
  
**回避策:** この問題を解決するには、再インストール時に別のインスタンス名を使用するか、再インストールする前にリソース グループを手動で削除してください。 詳細については、「 [SQL Server フェールオーバー クラスターでのノードの追加または削除](http://msdn.microsoft.com/library/ms191545)」をご覧ください。  
  
### <a name="12-choose-the-correct-file-to-download-and-install"></a>1.2 ダウンロードとインストールに使用する正しいファイルの選択  
ダウンロードとインストールに使用するファイルを確認するには、次の表を参照してください。 サービス パックをインストールする前に、システム要件を正しく満たしていることを確認します。 システム要件は、この表にあるリンクされたダウンロード ページに記載されています。  
  
|現在インストールされているバージョン|目的|ダウンロードとインストール|  
|-------------------------------------------|----------------------|---------------------------|  
|**32 ビット インストール:**|||  
|SQL Server 2012 のいずれかのエディションの 32 ビット バージョン|SQL Server 2012 SP1 の 32 ビット バージョンにアップグレード|SQLServer2012SP1-KB2674319-x86-ENU.exe ( [こちら](http://go.microsoft.com/fwlink/p/?LinkID=268158)から)|  
|SQL Server 2012 RTM Express の 32 ビット バージョン|SQL Server 2012 Express SP1 の 32 ビット バージョンにアップグレード|SQLServer2012SP1-KB2674319-x86-ENU.exe ( [こちら](http://go.microsoft.com/fwlink/p/?LinkID=268158)から)|  
|SQL Server 2012 のクライアントと管理ツールのみの 32 ビット バージョン (SQL Server 2012 Management Studio を含む)|SQL Server 2012 SP1 の 32 ビット バージョンにクライアントと管理ツールをアップグレード|SQLManagementStudio_x86_ENU.exe ( [こちら](http://go.microsoft.com/fwlink/p/?LinkID=267905)から)|  
|SQL Server 2012 Management Studio Express の 32 ビット バージョン|SQL Server 2012 SP1 Management Studio Express の 32 ビット バージョンにアップグレード|SQLManagementStudio_x86_ENU.exe ( [こちら](http://go.microsoft.com/fwlink/p/?LinkID=267905)から)|  
|SQL Server 2012 のいずれかのエディションの 32 ビット バージョン **および** クライアントと管理ツールの 32 ビット バージョン (SQL Server 2012 RTM Management Studio 含む)|SQL Server 2012 SP1 の 32 ビット バージョンにすべての製品をアップグレード|SQLServer2012SP1-KB2674319-x86-ENU.exe ( [こちら](http://go.microsoft.com/fwlink/p/?LinkID=268158)から)|  
|[Microsoft SQL Server 2012 RTM Feature Pack](http://www.microsoft.com/download/details.aspx?id=16978)の 1 つ以上のツールの 32 ビット バージョン|Microsoft SQL Server 2012 SP1 用 Feature Pack の 32 ビット バージョンにツールをアップグレード|[Microsoft SQL Server 2012 SP1 Feature Pack](http://go.microsoft.com/fwlink/p/?LinkID=268266)の 1 つ以上のファイル|  
|SQL Server 2012 の 32 ビット インストールなし|SP1 を含む 32 ビット バージョンの SQL Server 2012 をインストール (SP1 がプレインストールされた新しいインスタンス)|SQLServer2012SP1-FullSlipstream-x86-ENU.exe **および** SQLServer2012SP1-FullSlipstream-x86-ENU.box ( [こちら](http://go.microsoft.com/fwlink/p/?LinkID=268158)から)|  
|SQL Server 2012 Management Studio の 32 ビット インストールなし|32 ビットの SQL Server 2012 Management Studio をインストール (SP1 を含む)|SQLManagementStudio_x86_ENU.exe ( [こちら](http://go.microsoft.com/fwlink/p/?LinkId=267905)から)|  
|SQL Server 2012 RTM Express の 32 ビット バージョンなし|32 ビットの SQL Server 2012 Express をインストール (SP1 を含む)|SQLEXPR32_x86_ENU.exe ( [こちら](http://go.microsoft.com/fwlink/p/?LinkId=267905)から)|  
|**SQL Server 2008** または **SQL Server 2008 R2**の 32 ビット インストール|32 ビットの SQL Server 2012 (SP1 含む) に**インプレース アップグレード** |SQLServer2012SP1-FullSlipstream-x86-ENU.exe **および** SQLServer2012SP1-FullSlipstream-x86-ENU.box ( [こちら](http://go.microsoft.com/fwlink/p/?LinkID=268158)から)|  
|**64 ビット インストール:**|||  
|SQL Server 2012 のいずれかのエディションの 64 ビット バージョン|SQL Server 2012 SP1 の 64 ビット バージョンにアップグレード|SQLServer2012SP1-KB2674319-x64-ENU.exe ( [こちら](http://go.microsoft.com/fwlink/p/?LinkID=268158)から)|  
|SQL Server 2012 RTM Express の 64 ビット バージョン|SQL Server 2012 SP1 の 64 ビット バージョンにアップグレード|SQLServer2012SP1-KB2674319-x64-ENU.exe ( [こちら](http://go.microsoft.com/fwlink/p/?LinkID=268158)から)|  
|SQL Server 2012 のクライアントと管理ツールのみの 64 ビット バージョン (SQL Server 2012 Management Studio 含む)|SQL Server 2012 SP1 の 64 ビット バージョンにクライアントと管理ツールをアップグレード|SQLManagementStudio_x64_ENU.exe ( [こちら](http://go.microsoft.com/fwlink/p/?LinkID=267905)から)|  
|SQL Server 2012 Management Studio Express の 64 ビット バージョン|SQL Server 2012 SP1 Management Studio Express の 64 ビット バージョンにアップグレード|SQLManagementStudio_x64_ENU.exe ( [こちら](http://go.microsoft.com/fwlink/p/?LinkID=267905)から)|  
|SQL Server 2012 のいずれかのエディションの 64 ビット バージョン **および** クライアントと管理ツールの 64 ビット バージョン (SQL Server 2012 RTM Management Studio を含む)|SQL Server 2012 SP1 の 64 ビット バージョンにすべての製品をアップグレード|SQLServer2012SP1-KB2674319-x64-ENU.exe ( [こちら](http://go.microsoft.com/fwlink/p/?LinkID=268158)から)|  
|[Microsoft SQL Server 2012 RTM Feature Pack](http://www.microsoft.com/download/en/details.aspx?id=16978)の 1 つ以上のツールの 64 ビット バージョン|Microsoft SQL Server 2012 SP1 用 Feature Pack の 64 ビット バージョンにツールをアップグレード|[Microsoft SQL Server 2012 SP1 Feature Pack](http://go.microsoft.com/fwlink/p/?LinkID=268266)の 1 つ以上のファイル|  
|SQL Server 2012 の 64 ビット インストールなし|SP1 を含む 64 ビット バージョンの SQL Server 2012 をインストール (SP1 がプレインストールされた新しいインスタンス)|SQLServer2012SP1-FullSlipstream-x64-ENU.exe **および** SQLServer2012SP1-FullSlipstream-x64-ENU.box ( [こちら](http://go.microsoft.com/fwlink/p/?LinkID=268158)から)|  
|SQL Server 2012 Management Studio の 64 ビット インストールなし|64 ビットの SQL Server 2012 Management Studio をインストール (SP1 含む)|SQLManagementStudio_x64_ENU.exe ( [こちら](http://go.microsoft.com/fwlink/p/?LinkID=267905)から)|  
|SQL Server 2012 RTM Express の 64 ビット バージョンなし|64 ビットの SQL Server 2012 Express をインストール (SP1 含む)|SQLEXPR_x64_ENU.exe ( [こちら](http://go.microsoft.com/fwlink/p/?LinkID=267905)から)|  
|**SQL Server 2008** または **SQL Server 2008 R2**の 64 ビット インストール|64 ビットの SQL Server 2012 (SP1 含む) に**インプレース アップグレード** |SQLServer2012SP1-FullSlipstream-x64-ENU.exe **および** SQLServer2012SP1-FullSlipstream-x64-ENU.box ( [こちら](http://go.microsoft.com/fwlink/p/?LinkID=268158)から)|  
  
![[トップに戻る] リンクで使用される矢印アイコン](../sql-server/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")[内容](#bkmk_top)  
  
## <a name="bkmk_AS"></a>2.0 Analysis Services と PowerPivot  
  
### <a name="21-powerpivot-configuration-tool-does-not-create-the-powerpivot-gallery"></a>2.1 PowerPivot 構成ツールで PowerPivot ギャラリーが作成されない  
**問題点:** PowerPivot 構成ツールで準備されるのはチーム サイトであり、PowerPivot ギャラリーは作成されません。  
  
**回避策:** 新しいアプリ (ライブラリ) を作成します。  
  
1.  サイト コレクション機能の **[サイト コレクションの PowerPivot 機能の統合]** がアクティブになっていることを確認します。  
  
2.  既存のサイトの **[サイト コンテンツ]** ページで、 **[アプリの追加]**をクリックします。  
  
3.  **[PowerPivot ギャラリー]**をクリックします。  
  
### <a name="22-to-use-powerpivot-for-excel-with-excel-2013-you-must-use-the-add-in-that-is-installed-with-excel"></a>2.2 Excel 2013 で PowerPivot for Excel を使用する場合は Excel と一緒にインストールされたアドインを使用する必要がある  
**問題点:** Office 2010 では、PowerPivot for Excel は [http://www.microsoft.com/bi/powerpivot.aspx](http://www.microsoft.com/bi/powerpivot.aspx)からダウンロードできるスタンドアロンのアドインです。 このアドインは、 [Microsoft ダウンロード センター](http://www.microsoft.com/download/details.aspx?id=29074)からもダウンロードできます。 ダウンロードできる PowerPivot アドインの 2 つのバージョンがあることに注意してください。1つは SQL Server 2008 R2 に、もう 1 つは SQL Server 2012 にそれぞれ付属しています。 ただし、Office 2013 の場合、PowerPivot for Excel は Offce に付属していて、Excel のインストール時にインストールされます。 SQL Server 2008 R2 および SQL Server 2012 に付属の PowerPivot for Excel 2010 には Excel 2013 との互換性はありませんが、Excel 2010 と Excel 2013 をサイド バイ サイドで実行する場合は、クライアント コンピューターに PowerPivot for Excel 2010 をインストールできます。 つまり、2 つのバージョンの Excel が共存できるため、対応する PowerPivot アドインも共存できます。  
  
**回避策:** PowerPivot for Excel 2013 を使用するには、COM アドインを有効にする必要があります。 Excel 2013 で、 **[ファイル]** | **[オプション]** | **[アドイン]**の順にクリックします。**[管理]** ドロップダウン ボックスの一覧で **[COM アドイン]** を選択し、 **[設定]**をクリックします。 **[COM アドイン]**で、 **[Microsoft Office PowerPivot for Excel 2013]** を選択し、 **[OK]**をクリックします。  
  
![[トップに戻る] リンクで使用される矢印アイコン](../sql-server/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")[内容](#bkmk_top)  
  
## <a name="bkmk_RS"></a>3.0 Reporting Services  
  
### <a name="31-install-and-configure-sharepoint-server-2013-prior-to-installing-reporting-services"></a>3.1 Reporting Services をインストールする前に SharePoint Server 2013 をインストールおよび構成する  
**問題点:** SQL Server Reporting Services (SSRS) をインストールする **前に** 、次の要件を満たします。  
  
1.  SharePoint 2013 製品準備ツールを実行します。  
  
2.  SharePoint Server 2013 をインストールします。  
  
3.  SharePoint 2013 製品構成ウィザードを実行するか、同等の構成手順を完了して SharePoint ファームを構成します。  
  
**回避策:**  SharePoint ファームが構成される前に [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint モードをインストールした場合、必要な回避策は、インストールされている他のコンポーネントによって異なります。  
  
### <a name="32-power-view-in-sharepoint-server-2013-requires-microsoftanalysisservicesspclientdll"></a>3.2 SharePoint Server 2013 の Power View には Microsoft.AnalysisServices.SPClient.dll が必要  
**問題点:** [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] では、必須コンポーネントの **Microsoft.AnalysisServices.SPClient.dll** がインストールされません。 SharePoint Server 2013 Preview と [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] を SharePoint モードでインストールしても、PowerPivot for SharePoint 2013 インストーラー パッケージ (**spPowerPivot.msi**) をダウンロードしてインストールしないと、Power View は動作せず、Power View では次の現象が発生します。  
  
**現象:** Power View レポートを作成しようとすると、次のようなエラー メッセージが表示されます。  
  
-   "データ ソースへの接続を作成できません"  
  
内部エラーの詳細には、次のようなメッセージが含まれます。  
  
-   "値 'SharePoint Principal' は、接続文字列プロパティ 'User Identity' ではサポートされていません。"  
  
**回避策:** SharePoint Server 2013 に PowerPivot for SharePoint 2013 インストーラー パッケージ (**spPowerPivot.msi**) をインストールします。 インストーラー パッケージは、 [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] 機能パックに付属しています。 この機能パックは、 [!INCLUDE[msCoName](../includes/msconame-md.md)] ダウンロード センターの [SQL Server 2012 SP1 機能パック](http://go.microsoft.com/fwlink/p/?LinkID=268266)(http://go.microsoft.com/fwlink/p/?LinkID=268266) からダウンロードできます。  
  
### <a name="33-power-view-sheets-in-a-powerpivot-workbook-are-deleted-after-a-scheduled-data-refresh"></a>3.3 定期データ更新の後で、PowerPivot ブックの Power View シートが削除される  
**問題点**: PowerPivot for SharePoint アドインでは、Power View が含まれたブックで **定期データ更新** を使用すると、すべての Power View シートが削除されます。  
  
**回避策**: Power View ブックで **Scheduled Data Refresh** を使用するには、データ モデルだけの PowerPivot ブックを作成します。 Excel シートと Power View シートを含む別のブックを作成し、データ モデルを含む PowerPivot ブックにリンクします。 データ モデルを含む PowerPivot ブックに対してのみ、定期データ更新を実行します。  
  
## <a name="bkmk_DQS"></a>4.0 Data Quality Services  
  
### <a name="41-dqs-available-in-the-incorrect-edition-of-sql-server-2012"></a>4.1 DQS がサポートされていないエディションの SQL Server 2012 で使用可能になる  
**問題点:** [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] RTM リリースでは、Enterprise、Business Intelligence、および Developer 以外のエディションの SQL Server でも Data Quality Services (DQS) 機能を使用できます。 SQL Server 2012 SP1 のインストール後は、Enterprise、Business Intelligence、および Developer 以外のエディションで DQS を使用できなくなります。  
  
**回避策**: サポートされていないエディションで DQS を使用している場合は、サポートされているエディションにアップグレードするか、アプリケーションをこの機能に依存しないように変更します。  
  
![[トップに戻る] リンクで使用される矢印アイコン](../sql-server/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")[内容](#bkmk_top)  
  
## <a name="bkmk_Express"></a>5.0 SQL Server Express  
  
### <a name="51-full-version-of-sql-server-management-studio-available-in-sql-server-2012-express-sp1"></a>5.1 SQL Server 2012 Express SP1 で完全版の SQL Server Management Studio を使用可能  
SQL Server 2012 Express Service Pack 1 (SP1) リリースには、SQL Server 2012 Management Studio Express の代わりに、以前は SQL Server 2012 の DVD にしか収録されていなかった完全版の SQL Server 2012 Management Studio が含まれています。 SQL Server 2012 Express SP1 をダウンロードしてインストールする方法については、「 [SQL Server 2012 Express Service Pack 1](http://go.microsoft.com/fwlink/p/?linkid=267905)」を参照してください。  
  
![[トップに戻る] リンクで使用される矢印アイコン](../sql-server/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")[内容](#bkmk_top)  
  
## <a name="bkmk_CDC"></a>6.0 Change Data Capture Service for Oracle by Attunity と Change Data Capture Designer for Oracle by Attunity  
  
### <a name="61-upgrading-the-cdc-service-and-designer"></a>6.1 CDC Service および CDC Designer のアップグレード  
**問題点:** SQL Server 2012 SP1 をインストールする時点で、Change Data Capture Designer for Oracle および Change Data Capture Service for Oracle by Attunity がコンピューターにインストールされている場合、SP1 をインストールしてもこれらのコンポーネントはアップグレードされません。  
  
**回避策:** 次の手順に従って CDC コンポーネントを最新バージョンにアップグレードしてください。  
  
1.  [SQL Server 2012 SP1 Feature Pack ダウンロード ページ](http://go.microsoft.com/fwlink/p/?LinkID=268266)から Change Data Capture Service for Oracle by Attunity の .msi ファイルをダウンロードします。  
  
2.  .msi ファイルを実行します。  
  
![[トップに戻る] リンクで使用される矢印アイコン](../sql-server/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")[内容](#bkmk_top)  
  
## <a name="DACFx"></a>7.0 SQL Server Data-Tier Application Framework (DACFx)  
**インプレース アップグレードのサポート**  
  
このバージョンの Data-Tier Application Framework (DACFx) では、以前のバージョンからのインプレース アップグレードがサポートされているので、このリリースにアップグレードする前に以前の DACFx インストールを削除する必要はありません。 今後のリリースの DACFx は、 [ここ](https://msdn.microsoft.com/library/dn702988.aspx)にあります。  
  
**選択的 XML インデックスのサポート**  
  
SQL Server 2012 SP1 には、 [選択的 XML インデックス (SXI)](http://msdn.microsoft.com/en-us/598ecdcd-084b-4032-81b2-eed6ae9f5d44)のサポートが含まれています。これは SQL Server の新機能であり、高いパフォーマンスと効率で XML 列データのインデックスを作成できます。  
  
DACFx は、すべての DAC シナリオとクライアント ツールで、SXI インデックスをサポートするようになりました。 SXI がサポートされるのは、最新のバージョンの SSDT のみです。 SSDT RTM バージョンおよび September 2012 バージョンでは、SXI はサポートされません。  
  
**ネイティブ BCP データ形式のサポート**  
  
以前は、テーブル データを DACPAC パッケージおよび BACPAC パッケージ内に格納するために使用されるデータ形式は JSON でした。 今回の更新により、データ保存形式がネイティブ BCP になりました。 この変更によって、SQL_Variant 型のサポートなど、DACFx に対する SQL Server データ型の忠実度が向上し、大規模なデータベースのデータ配置のパフォーマンスが強化されました。  
  
**パッケージの作成/配置時における CHECK 制約状態の保持**  
  
従来、DACFx はデータベース スキーマ内のテーブルで定義された CHECK 制約の状態 (WITH CHECK/NOCHECK) を保持せず、この情報を DACPAC 内に格納しませんでした。 この動作により、CHECK 制約に違反している既存のテーブル データがある場合に、パッケージ配置の問題が発生することがありました。 今回の更新により、DACFx が現在の CHECK 制約の状態を、データベースから抽出するときに DACPAC 内に格納し、パッケージの配置時に適切に復元するようになりました。  
  
**SqlPackage.exe (DACFx コマンド ライン ツール) に対する更新**  
  
-   データを含む DACPAC の抽出: データベース スキーマの他にユーザー テーブルのデータを含むライブ SQL Server または Windows Azure SQL データベースから、データベース スナップショット ファイル (.dacpac) を作成します。 これらのパッケージは、SqlPackage.exe の Publish 操作を使用して、新規または既存の SQL Server または Windows Azure SQL データベースにパブリッシュできます。 パッケージに含まれているデータによって、ターゲット データベースの既存のデータは置き換えられます。  
  
-   BACPAC のエクスポート: オンプレミス SQL Server から Windows Azure SQL データベースへのデータベースの移行に使用できる、データベース スキーマおよびユーザー データを含むライブ SQL Server または Windows Azure SQL データベースの論理バックアップ ファイル (.bacpac) を作成します。 サポートされているバージョンの SQL Server 間で、Azure と互換性のあるデータベースをエクスポートし、後でインポートできます。  
  
-   BACPAC のインポート: .bacpac ファイルをインポートして、SQL Server または Windows Azure SQL データベースを新規に作成したり、空のデータベースにデータを入力したりできます。  
  
SqlPackage.exe の完全なドキュメントは、MSDN の [ここ](http://msdn.microsoft.com/library/hh550080%28v=vs.103%29.aspx)にあります。  
  
**パッケージの互換性**  
  
今回のリリースでは、DAC パッケージの上位互換性シナリオが複数導入されています。  
  
-   今回のリリースで作成された、SXI 要素もテーブル データも含まない DAC パッケージは、以前のリリースの DACFx (SQL Server 2012 RTM、SQL Server 2012 CU1、および DACFx September 2012) で使用できます。  
  
-   以前のバージョンの DACFx で作成されたすべての DAC パッケージを、このリリースで使用できます。  
  
## <a name="bkmk_known_issues_fixed"></a>8.0 この Service Pack で修正された既知の問題  
この Service Pack で修正されたすべてのバグと既知の問題については、 [サポート技術情報記事](http://support.microsoft.com/kb/2674319)を参照してください。  
  
[目次](#bkmk_top)  
  
## <a name="see-also"></a>参照  
[SQL Server のバージョンとエディションを確認する方法](http://support.microsoft.com/kb/321185)  
[SQL Server 2014 の各エディションがサポートする機能](http://msdn.microsoft.com/en-us/5da61ff5-12b9-48e6-b3c8-0dacca1751c4)  
  
