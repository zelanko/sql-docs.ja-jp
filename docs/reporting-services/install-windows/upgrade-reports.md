---
title: "レポートのアップグレード |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reports [Reporting Services], upgrading
- published reports [Reporting Services], upgrades
- custom report items, upgrading
- Reporting Services, upgrades
- upgrading Reporting Services
- snapshots [Reporting Services], upgrading
- report definition files [Reporting Services]
- .rdl files
ms.assetid: a1a10c67-7462-4562-9b07-a8822188a161
caps.latest.revision: 70
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 5c6265fd62ae10a8037b0fbd1f7d26edb5de8bc9
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---

# <a name="upgrade-reports"></a>レポートのアップグレード

[!INCLUDE[ssrs-appliesto-sql2016-preview](../../includes/ssrs-appliesto-sql2016-preview.md)]

  レポート定義 (.rdl) ファイルは、次の方法で開いたときに自動的にアップグレードされます。  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のレポート デザイナーでレポートを開くと、レポート定義は現在サポートされている RDL スキーマにアップグレードされます。 プロジェクトのプロパティで [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] レポート サーバーを指定すると、レポート定義はターゲット サーバーと互換性のあるスキーマに保存されます。  
  
-   既にインストールされている [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] にアップグレードすると、レポート サーバーにパブリッシュされている既存のレポートとスナップショットは、最初に処理されるときにコンパイルされ、新しいスキーマへと自動的にアップグレードされます。 レポートを自動的にアップグレードできない場合、レポートは下位互換性モードを使用して処理されます。 レポート定義は元のスキーマのまま残ります。  
  
 レポート定義ファイルをレポート サーバーまたは SharePoint サイトに直接アップロードする場合、レポートはアップグレードされません。 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] でレポート定義をアップグレードしない限り、.rdl ファイルはアップグレードされません。  
  
 レポートをローカルでアップグレードした後、またはレポート サーバーでアップグレードした後で、エラー、警告、およびメッセージがさらに通知される場合があります。 これは、内部のレポート オブジェクト モデルと処理コンポーネントが変更されたために、レポートに潜んでいた問題が検出され、メッセージが出力されるようになったものです。 詳細については、[Reporting Services Backward Compatibility] を参照してください[](../../reporting-services/reporting-services-backward-compatibility.md "旧バージョンとの互換性 |。Reporting Services")です。  
  
 新機能の詳細については[!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]を参照してください[Reporting Services の新](https://msdn.microsoft.com/library/ms170438.aspx)です。  

##  <a name="bkmk_versionsupported"></a> アップグレード可能なバージョン  
 以前のどのバージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] で作成されたレポートもアップグレードできます。 以下のバージョンがあります。  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
##  <a name="bkmk_rdlfiles"></a> レポート定義 (.rdl) ファイルとレポート デザイナー  
 レポート定義ファイルには、.rdl ファイルの検証に使用するレポート定義スキーマのバージョンを示す RDL 名前空間への参照が含まれています。  
  
 以前の名前空間に対応するレポートが作成済みの場合、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のレポート デザイナーで .rdl ファイルを開くと、レポート デザイナーによって自動的にバックアップ ファイルが作成され、レポートが現在の名前空間にアップグレードされます。 これは、レポート定義ファイルをアップグレードする唯一の方法です。  
  
 設定する配置プロパティは、レポート定義ファイルを保存するスキーマに影響する場合があります。 詳細については、「 [SQL Server データ ツールの配置およびバージョン サポート (SSRS)](../../reporting-services/tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)には含まれていません。  
  
 以前のバージョンで作成された .rdl ファイルをアップロードする[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]して、新しいバージョンに自動的にアップグレード初回使用時にします。 レポート サーバーには、元の形式のレポート定義ファイルが格納されます。 レポートは初めて表示されたときに自動的にアップグレードされますが、格納されたレポート定義ファイルは変更されません。  
  
 レポート、レポート サーバー、またはレポート デザイナーの現在の RDL スキーマを確認するには、「[レポート定義スキーマのバージョンを確認する &#40;SSRS&#41;](../../reporting-services/reports/find-the-report-definition-schema-version-ssrs.md)」を参照してください。  
  
##  <a name="bkmk_publishedreports_and_snapshots"></a> パブリッシュされたレポートおよびレポートのスナップショット  
 既存のパブリッシュされたレポートおよびレポートのスナップショットは、初めて使用するときに、レポート サーバーによって新しいレポート定義スキーマへのアップグレードが試行されます。ユーザーは何も処理する必要はありません。 ユーザーがレポートまたはレポートのスナップショットを表示するか、レポート サーバーがサブスクリプションを処理すると、アップグレードが試行されます。 レポート定義は置き換えられませんが、引き続き、元のスキーマでレポート サーバーに保存されます。 レポートをアップグレードできない場合、レポートは下位互換性モードで実行されます。  
  
##  <a name="bkmk_backcompat"></a> 下位互換性モード  
 正常にアップグレードされたレポートは、 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] レポート プロセッサによって処理されます。 アップグレードできないレポートは、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート プロセッサによって下位互換性モードで処理されます。 レポートを両方のレポート プロセッサで処理することはできません。 レポートは、初めて使用するときに、正常にアップグレードされるか、下位互換性モードの対象としてマークされます。  
  
 新しい機能をサポートするのは、 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] レポート プロセッサのみです。 レポートをアップグレードできない場合でも表示レポートは表示できますが、新しい機能は利用できません。 新しい機能を利用するには、レポートが正常にアップグレードされる必要があります。  
  
##  <a name="bkmk_subreports"></a> サブレポートを含むレポートのアップグレード  
 レポートにサブレポートが含まれている場合、アップグレード時に次の 4 つのうちのいずれかの状態になります。  
  
-   メイン レポートおよびすべてのサブレポートを正常にアップグレードできる。 レポートは [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] レポート プロセッサで処理されます。  
  
-   メイン レポートおよびすべてのサブレポートをアップグレードできない。 レポートは [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、 or [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート プロセッサによって処理されます。  
  
-   メイン レポートはアップグレードできるが、1 つ以上のサブレポートをアップグレードできない。 メイン レポートは [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] レポート プロセッサで処理されますが、表示されたレポート内のアップグレードできなかったサブレポートの表示位置に "エラー: サブレポートを処理できませんでした" というメッセージが表示されます。  
  
-   メイン レポートはアップグレードできないが、1 つ以上のサブレポートをアップグレードできる。 メイン レポートは [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] レポート プロセッサで処理されますが、表示されたレポート内のサブレポートの表示位置に "エラー: サブレポートを処理できませんでした" というメッセージが表示されます。  
  
 "エラー: サブレポートを処理できませんでした" というエラーが表示された場合、レポートを同一バージョンのレポート プロセッサで処理できるように、メイン レポートまたはサブレポートの定義を変更する必要があります。  
  
 詳細レポートは独立したレポートとして処理されるため、詳細レポートにはこの制限はありません。  
  
##  <a name="bkmk_CRIs"></a> カスタム レポート アイテムを含むレポートのアップグレード  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)][!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートには、サードパーティのソフトウェア ベンダーによって提供され、システム管理者によってレポート作成コンピューターおよびレポート サーバーにインストールされたカスタム レポート アイテム (CRI) が含まれている場合があります。 CRI を含むレポートは次の方法でアップグレードできます。  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーを [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] レポート サーバーにアップグレードします。 レポート サーバー上のパブリッシュされたレポートが、初めて使用するときに自動的にアップグレードされます。  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートを [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] レポート サーバーにアップロードします。 レポートが、初めて使用するときに自動的にアップグレードされます。  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートを [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のレポート デザイナーで開きます。 元のレポートのバックアップ コピーが作成されます。 以下の 2 つのうちのいずれかの状況になります。  
  
    1.  レポート内のどの CRI にも、サポートされていない機能が含まれていない。 CRI が新しいレポート定義スキーマのレポート アイテムに変換され、レポート全体がアップグレードされます。 ファイルを保存すると、現在の RDL 名前空間で保存されます。  
  
    2.  レポート内の 1 つ以上の CRI に、サポートされていない機能が含まれている。 CRI を変換するか、変更せずにそのまま使用するかを指定するためのダイアログ ボックスが表示されます。  
  
     詳細については、このトピックの「 [レポート デザイナーで CRI を含むレポートを開く](#OpeningaReport) 」を参照してください。  
  
 レポート サーバー、[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]、またはレポートの現在の RDL 名前空間を確認する方法については、「[レポート定義スキーマのバージョンを確認する &#40;SSRS&#41;](../../reporting-services/reports/find-the-report-definition-schema-version-ssrs.md)」を参照してください。  
  
### <a name="upgrading-reports-on-a-report-server"></a>レポート サーバー上のレポートのアップグレード  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーにアップグレードしたレポート サーバーで初めて [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] レポートを実行すると、そのレポートは、レポート サーバーでサポートされている現在のレポート定義の名前空間に自動的にアップグレードされます。 アップグレード前にレポート サーバーに存在していたレポートと、レポート マネージャーを使用してアップロードされたか、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]のレポート デザイナーからレポート サーバーにパブリッシュされたレポートが含まれます。  
  
 次の表に、レポート内の CRI の種類ごとに、レポート サーバーで実行されるアップグレード操作を示します。  
  
|CRI の種類|レポート サーバーによるアップグレード操作|  
|--------------|----------------------------------|  
|サードパーティの CRI|アップグレードは実行されません。<br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート プロセッサで処理されます。|  
  
###  <a name="OpeningaReport"></a> レポート デザイナーで CRI を含むレポートを開く  
 開くと、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]のレポート デザイナーで Cri を含むレポート[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]レポートは、新しいレポート定義スキーマにアップグレードされます。 レポートに含まれる CRI に応じて、次のいずれかの操作が実行されます。  
  
-   サードパーティの CRI が検出された。 レポート作成コンピューターにインストールされた CRI のバージョンが新しい RDL スキーマと互換性がない場合、デザイン画面に赤い X マークのテキスト ボックスが表示されます。システム管理者に相談して、新しい RDL スキーマと互換性がある新しいバージョンのサードパーティ ベンダーの CRI をインストールする必要があります。  
  
 レポート作成環境でレポートをアップグレード後に保存する以外に、既存のレポートを新しいレポート定義スキーマにアップグレードする方法はありません。  
  
###  <a name="bkmk_convertCRIdialog"></a> [CRI の変換] ダイアログ ボックス  
 このレポートにはサポートされていない機能を持つカスタム レポート アイテム (CRI) が含まれています。 CRI は、レポートにデータを表示するカスタム オブジェクトをサポートするレポート定義言語 (RDL) の拡張機能です。 CRI には、サードパーティのソフトウェア ベンダーによって提供されるデザイン時コンポーネントおよび実行時コンポーネントが含まれます。  
  
> [!NOTE]  
>  システム管理者は、レポート サーバーでカスタム レポートをサポートするかどうかを選択します。 レポートで CRI を表示するには、CRI コンポーネントをレポートのプレビューのためにレポート作成クライアントに、およびパブリッシュまたはアップロードされたレポートを表示するためにレポート サーバーにインストールする必要があります。 詳細については、「 [カスタム レポート アイテム](../../reporting-services/custom-report-items/custom-report-items.md) 」、およびサードパーティのソフトウェア ベンダーのマニュアルを参照してください。  
  
 新しいレポート定義形式のレポート アイテムに変換できる CRI もあります。 次の一覧に従って、このレポートの CRI を変換するかどうかを決定します。  
  
-   **[する]** 可能であればレポート内のすべての CRI を変換する場合に、 **[する]** を選択します。 CRI でサポートされていない機能はアップグレードできません。レポート定義ファイルから削除されます。 レポートを表示すると、CRI がレポートに表示される方法に違いが見られます。  
  
-   **[しない]** レポートの CRI を変換しない場合に **[しない]** を選択します。 現在のバージョンでは、レポート プロセッサはこれらの CRI を表示できません。 システム管理者が、サードパーティのソフトウェア ベンダーから新しいレポート定義形式と互換性のある CRI の新しいバージョンのインストールを計画している場合、 **しない**を選択する必要があります。 新しいバージョンが使用可能になるまで、CRI はレポート内で赤い X のある空白テキスト ボックスとして表示されます。  
  
 どちらの場合、レポートは、新しいレポート定義形式にアップグレードされ、として、元のレポートのバックアップ コピーを保存*\<レポート名 >* `-` Backup.rdl です。 レポート作成ツールにレポートを保存する場合、新しいレポート定義形式でアップグレードされたレポートを保存することになります。 レポートをパブリッシュする場合、レポートはまずコンピューターに保存され、それからレポート サーバーにパブリッシュされます。 レポートのアップグレード バージョンをレポート サーバーにパブリッシュします。  
  
 レポートを保存しない場合、元のレポートは変更されません。 ただし、SQL Server 2016 のバージョンのでは、このレポートを編集することはできません[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]か、レポートを新しいレポート定義形式を使用している環境を作成します。 アップロードして、レポートの元のバージョンを実行を続行することができます、 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] web ポータルを使用してレポート サーバー。 詳細については、次を参照してください。 [Web ポータル](../../reporting-services/web-portal-ssrs-native-mode.md)です。  
  
 レポートをレポート サーバーにパブリッシュする代わりに、アップロードする場合、レポート プロセッサはそのレポートを最初の使用時にアップグレードできるかどうかを決定します。 アップグレードできないレポートは下位互換性モードで処理され、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]の以前のバージョンと同じように表示されます。  

## <a name="next-steps"></a>次の手順

[Reporting Services のアップグレードと移行](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)   
[SQL Server 2016 における SQL Server Reporting Services における重大な変更](../../analysis-services/behavior-changes-to-analysis-services-features-in-sql-server-2016.md)   
[SQL Server 2016 における SQL Server Reporting Services の動作変更します。](../../analysis-services/behavior-changes-to-analysis-services-features-in-sql-server-2016.md)   
[SQL Server Reporting Services SQL Server 2016 で廃止された機能](../../reporting-services/behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
[カスタム レポート アイテム](../../reporting-services/custom-report-items/custom-report-items.md)   
[レポート サーバー データベースをアップグレードします。](../../reporting-services/install-windows/upgrade-a-report-server-database.md)  

他に質問しますか。 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)
