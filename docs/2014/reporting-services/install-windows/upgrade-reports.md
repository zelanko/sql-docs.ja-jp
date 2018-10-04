---
title: レポートのアップグレード | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
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
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 1caf710a55ee548f7939ec65ead6397ccd4092d4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48179322"
---
# <a name="upgrade-reports"></a>Upgrade Reports
  レポート定義 (.rdl) ファイルは、次の方法で開いたときに自動的にアップグレードされます。  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のレポート デザイナーでレポートを開くと、レポート定義は現在サポートされている RDL スキーマにアップグレードされます。 指定した場合、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]または[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]レポート サーバー プロジェクトのプロパティで、レポート定義は、ターゲット サーバーと互換性のあるスキーマに保存されます。  
  
-   既にインストールされている [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] にアップグレードすると、レポート サーバーにパブリッシュされている既存のレポートとスナップショットは、最初に処理されるときにコンパイルされ、新しいスキーマへと自動的にアップグレードされます。 レポートを自動的にアップグレードできない場合、レポートは下位互換性モードを使用して処理されます。 レポート定義は元のスキーマのまま残ります。  
  
 レポート定義ファイルをレポート サーバーまたは SharePoint サイトに直接アップロードする場合、レポートはアップグレードされません。 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] でレポート定義をアップグレードしない限り、.rdl ファイルはアップグレードされません。  
  
 レポートをローカルでアップグレードした後、またはレポート サーバーでアップグレードした後で、エラー、警告、およびメッセージがさらに通知される場合があります。 これは、内部のレポート オブジェクト モデルと処理コンポーネントが変更されたために、レポートに潜んでいた問題が検出され、メッセージが出力されるようになったものです。 詳細については、「 [Reporting Services Backward Compatibility](../reporting-services-backward-compatibility.md)」をご参照ください。  
  
 新機能の詳細については[!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]を参照してください[新&#40;Reporting Services&#41;](../what-s-new-reporting-services.md)します。  
  
 このトピックの内容  
  
-   [アップグレード可能なバージョン](#bkmk_versionsupported)  
  
-   [レポート定義 (.rdl) ファイルとレポート デザイナー](#bkmk_rdlfiles)  
  
-   [パブリッシュされたレポートおよびレポートのスナップショット](#bkmk_publishedreports_and_snapshots)  
  
-   [下位互換性モード](#bkmk_backcompat)  
  
-   [サブレポートを含むレポートのアップグレード](#bkmk_subreports)  
  
-   [カスタム レポート アイテムを含むレポートのアップグレード](#bkmk_CRIs)  
  
-   [[CRI の変換] ダイアログ ボックス](#bkmk_convertCRIdialog)  
  
##  <a name="bkmk_versionsupported"></a> アップグレード可能なバージョン  
 以前のどのバージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] で作成されたレポートもアップグレードできます。 以下のバージョンがあります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 Service pack 1  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 (Service Pack 2 適用済み)  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
##  <a name="bkmk_rdlfiles"></a> レポート定義 (.rdl) ファイルとレポート デザイナー  
 レポート定義ファイルには、.rdl ファイルの検証に使用するレポート定義スキーマのバージョンを示す RDL 名前空間への参照が含まれています。  
  
 以前の名前空間に対応するレポートが作成済みの場合、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のレポート デザイナーで .rdl ファイルを開くと、レポート デザイナーによって自動的にバックアップ ファイルが作成され、レポートが現在の名前空間にアップグレードされます。 これは、レポート定義ファイルをアップグレードする唯一の方法です。  
  
 設定する配置プロパティは、レポート定義ファイルを保存するスキーマに影響する場合があります。 詳細については、「[SQL Server データ ツールの配置およびバージョン サポート &#40;SSRS&#41;](../tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)」を参照してください。  
  
 以前のバージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] で作成された .rdl ファイルは [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] レポート サーバーにアップロードすることができ、初めて使用するときに自動的にアップグレードされます。 レポート サーバーには、元の形式のレポート定義ファイルが格納されます。 レポートは初めて表示されたときに自動的にアップグレードされますが、格納されたレポート定義ファイルは変更されません。  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] レポート定義の名前空間を含むレポートは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 レポート サーバーにパブリッシュまたはアップロードできません。  
  
 レポート、レポート サーバー、またはレポート デザイナーの現在の RDL スキーマを確認するには、「[レポート定義スキーマのバージョンを確認する &#40;SSRS&#41;](../reports/find-the-report-definition-schema-version-ssrs.md)」を参照してください。  
  
##  <a name="bkmk_publishedreports_and_snapshots"></a> パブリッシュされたレポートおよびレポートのスナップショット  
 既存のパブリッシュされたレポートおよびレポートのスナップショットは、初めて使用するときに、レポート サーバーによって新しいレポート定義スキーマへのアップグレードが試行されます。ユーザーは何も処理する必要はありません。 ユーザーがレポートまたはレポートのスナップショットを表示するか、レポート サーバーがサブスクリプションを処理すると、アップグレードが試行されます。 レポート定義は置き換えられませんが、元のスキーマのまま [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] レポート サーバーに格納されます。 レポートをアップグレードできない場合、レポートは下位互換性モードで実行されます。  
  
##  <a name="bkmk_backcompat"></a> 下位互換性モード  
 正常にアップグレードされたレポートは、 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] レポート プロセッサによって処理されます。 アップグレードできないレポートは処理、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]レポート プロセッサでは、下位互換性モード。 レポートを両方のレポート プロセッサで処理することはできません。 レポートは、初めて使用するときに、正常にアップグレードされるか、下位互換性モードの対象としてマークされます。  
  
 新しい機能をサポートするのは、 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] レポート プロセッサのみです。 レポートをアップグレードできない場合でも表示レポートは表示できますが、新しい機能は利用できません。 新しい機能を利用するには、レポートが正常にアップグレードされる必要があります。  
  
##  <a name="bkmk_subreports"></a> サブレポートを含むレポートのアップグレード  
 レポートにサブレポートが含まれている場合、アップグレード時に次の 4 つのうちのいずれかの状態になります。  
  
-   メイン レポートおよびすべてのサブレポートを正常にアップグレードできる。 レポートは [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] レポート プロセッサで処理されます。  
  
-   メイン レポートおよびすべてのサブレポートをアップグレードできない。 によって処理される、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]レポート プロセッサ。  
  
-   メイン レポートはアップグレードできるが、1 つ以上のサブレポートをアップグレードできない。 メイン レポートは [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] レポート プロセッサで処理されますが、表示されたレポート内のアップグレードできなかったサブレポートの表示位置に "エラー: サブレポートを処理できませんでした" というメッセージが表示されます。  
  
-   メイン レポートはアップグレードできないが、1 つ以上のサブレポートをアップグレードできる。 メイン レポートは [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] レポート プロセッサで処理されますが、表示されたレポート内のサブレポートの表示位置に "エラー: サブレポートを処理できませんでした" というメッセージが表示されます。  
  
 "エラー: サブレポートを処理できませんでした" というエラーが表示された場合、レポートを同一バージョンのレポート プロセッサで処理できるように、メイン レポートまたはサブレポートの定義を変更する必要があります。  
  
 詳細レポートは独立したレポートとして処理されるため、詳細レポートにはこの制限はありません。  
  
##  <a name="bkmk_CRIs"></a> カスタム レポート アイテムを含むレポートのアップグレード  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートには、サードパーティのソフトウェア ベンダーによって提供され、システム管理者によってレポート作成コンピューターおよびレポート サーバーにインストールされたカスタム レポート アイテム (CRI) が含まれている場合があります。 CRI を含むレポートは次の方法でアップグレードできます。  
  
-   A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]はレポート サーバーをアップグレードする[!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]レポート サーバー。 レポート サーバー上のパブリッシュされたレポートが、初めて使用するときに自動的にアップグレードされます。  
  
-   A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]にレポートをアップロード、[!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]レポート サーバー。 レポートが、初めて使用するときに自動的にアップグレードされます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートを [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のレポート デザイナーで開きます。 元のレポートのバックアップ コピーが作成されます。 以下の 2 つのうちのいずれかの状況になります。  
  
    1.  レポート内のどの CRI にも、サポートされていない機能が含まれていない。 CRI が新しいレポート定義スキーマのレポート アイテムに変換され、レポート全体がアップグレードされます。 ファイルを保存すると、現在の RDL 名前空間で保存されます。  
  
    2.  レポート内の 1 つ以上の CRI に、サポートされていない機能が含まれている。 CRI を変換するか、変更せずにそのまま使用するかを指定するためのダイアログ ボックスが表示されます。  
  
     詳細については、このトピックの「 [レポート デザイナーで CRI を含むレポートを開く](#OpeningaReport) 」を参照してください。  
  
 レポート サーバー、[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]、またはレポートの現在の RDL 名前空間を確認する方法については、「[レポート定義スキーマのバージョンを確認する &#40;SSRS&#41;](../reports/find-the-report-definition-schema-version-ssrs.md)」を参照してください。  
  
### <a name="upgrading-reports-on-a-report-server"></a>レポート サーバー上のレポートのアップグレード  
 最初に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]にアップグレードされたレポート サーバーでレポートを実行、[!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]レポート サーバー、レポートがレポート サーバーでサポートされている現在のレポート定義名前空間に自動的にアップグレードします。 レポートが、アップグレードする前に、レポート サーバーに存在していた可能性がありますが、またはがレポート マネージャーを使用してアップロードまたはレポート デザイナーからレポート サーバーにパブリッシュされたレポートがでした[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]します。  
  
 次の表に、レポート内の CRI の種類ごとに、レポート サーバーで実行されるアップグレード操作を示します。  
  
|CRI の種類|レポート サーバーによるアップグレード操作|  
|--------------|----------------------------------|  
|サードパーティの CRI|アップグレードは実行されません。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート プロセッサで処理されます。|  
|サポートされていない機能がない Dundas 2005 のグラフ CRI|最新の RDL スキーマにアップグレードされます。 Dundas 2005 のすべてのグラフ CRI が、[!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] と互換性のあるグラフ データ領域に変換されます。<br /><br /> [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] レポート プロセッサで処理されます。|  
|サポートされていない機能がない Dundas 2005 のゲージ CRI|最新の RDL スキーマにアップグレードされます。 Dundas 2005 のすべてのゲージ Cri と互換性のあるデータ領域をゲージに変換されます。 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]<br /><br /> [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] レポート プロセッサで処理されます。|  
|サポートされていない機能を含む Dundas 2005 のグラフ CRI|アップグレードは実行されません。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート プロセッサで処理されます。|  
|サポートされていない機能を含む Dundas 2005 のゲージ CRI|アップグレードは実行されません。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート プロセッサで処理されます。|  
  
###  <a name="OpeningaReport"></a> レポート デザイナーで CRI を含むレポートを開く  
 開くと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]レポートのレポート デザイナーで cri を含む[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]レポートは、新しいレポート定義スキーマにアップグレードされます。 レポートに含まれる CRI に応じて、次のいずれかの操作が実行されます。  
  
-   サードパーティの CRI が検出された。 レポート作成コンピューターにインストールされた CRI のバージョンが新しい RDL スキーマと互換性がない場合、デザイン画面に赤い X マークのテキスト ボックスが表示されます。システム管理者に相談して、新しい RDL スキーマと互換性がある新しいバージョンのサードパーティ ベンダーの CRI をインストールする必要があります。  
  
-   Dundas 2005 のグラフまたはゲージ CRI が検出され、すべてのインスタンスがサポートされている機能で構成されている。 Dundas 2005 のすべてのグラフおよびゲージ CRI が、ツールボックスに表示される Reporting Services のグラフおよびゲージ レポート アイテムに変換されます。 これらは、ネイティブなグラフおよびゲージ レポート アイテムと呼ばれます。  
  
-   Dundas 2005 のグラフまたはゲージ CRI が検出され、サポートされていない機能を含むインスタンスがある。 サポートされていない機能については、次のセクションで説明します。 すべての CRI をネイティブ レポート アイテムに変換するかどうかを選択できます。  
  
    -   変換する場合、レポートが新しい RDL スキーマにアップグレードされ、Dundas 2005 のグラフおよびゲージ CRI が対応するネイティブなグラフおよびゲージ レポート アイテムに変換されますが、サポートされていない機能は削除されません。 表示レポートでの CRI による表示方法が異なる場合があります。  
  
    -   変換しない場合、レポートは新しい RDL スキーマに変換されますが、CRI はサードパーティの CRI として扱われます。 システム管理者およびサードパーティ ベンダーに相談して、新しいレポート スキーマと互換性がある新しい CRI をインストールする必要があります。 新しい CRI が利用できない場合は、レポート デザイナーで、レポートに赤い X マークのテキスト ボックスが表示されます。  
  
 レポート作成環境でレポートをアップグレード後に保存する以外に、既存のレポートを新しいレポート定義スキーマにアップグレードする方法はありません。  
  
### <a name="unsupported-dundas-2005-chart-custom-report-item-functionality"></a>サポートされていない Dundas 2005 のグラフ カスタム レポート アイテム機能  
 Dundas 2005 のグラフ CRI のサポートされていない機能には、次の機能があります。  
  
-   注釈  
  
-   カスタムの凡例アイテム  
  
-   次の名前のカスタム属性:  
  
    -   CUSTOM_CODE_CS  
  
    -   CUSTOM_CODE_VB  
  
    -   CUSTOM_CODE_COMPILED_ASSEMBLY  
  
         たとえば、.rdl ファイルに次のようなセクションが含まれている場合、アップグレード前に削除する必要があります。  
  
        ```  
        <CustomProperty>  
         <Name>CUSTOM_CODE_CS</Name>  
         <Value>dXNpWERwegfdfgiobxxl3bmc… </Value>  
        </CustomProperty>  
        ```  
  
### <a name="unsupported-dundas-2005-gauge-custom-report-item-functionality"></a>サポートされていない Dundas 2005 のゲージ カスタム レポート アイテム機能  
 Dundas 2005 のゲージ CRI のサポートされていない機能には、次の機能があります。  
  
-   数値インジケーター  
  
-   状態インジケーター  
  
-   カスタム イメージ  
  
###  <a name="bkmk_convertCRIdialog"></a> [CRI の変換] ダイアログ ボックス  
 このレポートにはサポートされていない機能を持つカスタム レポート アイテム (CRI) が含まれています。 CRI は、レポートにデータを表示するカスタム オブジェクトをサポートするレポート定義言語 (RDL) の拡張機能です。 CRI には、サードパーティのソフトウェア ベンダーによって提供されるデザイン時コンポーネントおよび実行時コンポーネントが含まれます。  
  
> [!NOTE]  
>  システム管理者は、レポート サーバーでカスタム レポートをサポートするかどうかを選択します。 レポートで CRI を表示するには、CRI コンポーネントをレポートのプレビューのためにレポート作成クライアントに、およびパブリッシュまたはアップロードされたレポートを表示するためにレポート サーバーにインストールする必要があります。 詳細については、次を参照してください。[カスタム レポート アイテム](../custom-report-items/custom-report-items.md)とサード パーティのソフトウェア ベンダーのマニュアルをします。  
  
 新しいレポート定義形式のレポート アイテムに変換できる CRI もあります。 変換できる Cri の一覧で、次を参照してください。[レポートのアップグレード](upgrade-reports.md)します。 次の一覧に従って、このレポートの CRI を変換するかどうかを決定します。  
  
-   **[する]** 可能であればレポート内のすべての CRI を変換する場合に、 **[する]** を選択します。 CRI でサポートされていない機能はアップグレードできません。レポート定義ファイルから削除されます。 サポートされていない機能の一覧で、次を参照してください。[レポートのアップグレード](upgrade-reports.md)します。 レポートを表示すると、CRI がレポートに表示される方法に違いが見られます。  
  
-   **[しない]** レポートの CRI を変換しない場合に **[しない]** を選択します。 現在のバージョンでは、レポート プロセッサはこれらの CRI を表示できません。 システム管理者が、サードパーティのソフトウェア ベンダーから新しいレポート定義形式と互換性のある CRI の新しいバージョンのインストールを計画している場合、 **しない**を選択する必要があります。 新しいバージョンが使用可能になるまで、CRI はレポート内で赤い X のある空白テキスト ボックスとして表示されます。  
  
 どちらの場合でも、レポートは新しいレポート定義形式にアップグレードされ、元のレポートのバックアップ コピーは *\<Report Name>* `-` Backup.rdl として保存されます。 レポート作成ツールにレポートを保存する場合、新しいレポート定義形式でアップグレードされたレポートを保存することになります。 レポートをパブリッシュする場合、レポートはまずコンピューターに保存され、それからレポート サーバーにパブリッシュされます。 レポートのアップグレード バージョンをレポート サーバーにパブリッシュします。  
  
 レポートを保存しない場合、元のレポートは変更されません。 ただし、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] バージョン、または新しいレポート定義形式を使用するレポート作成環境では、このレポートは編集できません。 レポート マネージャーを使用して [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] レポート サーバーにアップロードすることで、レポートの元のバージョンを継続して実行できます。 詳細については、「[ファイルまたはレポートのアップロード &#40;レポート マネージャー&#41;](../reports/upload-a-file-or-report-report-manager.md)」を参照してください。  
  
 レポートをレポート サーバーにパブリッシュする代わりに、アップロードする場合、レポート プロセッサはそのレポートを最初の使用時にアップグレードできるかどうかを決定します。 アップグレードできないレポートは下位互換性モードで処理され、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の以前のバージョンと同じように表示されます。  
  
## <a name="see-also"></a>参照  
 [Reporting Services のアップグレードと移行](upgrade-and-migrate-reporting-services.md)   
 [SQL Server 2014 における SQL Server Reporting Services における重大な変更](../breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)   
 [SQL Server 2014 における SQL Server Reporting Services の動作変更します。](../behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
 [SQL Server Reporting Services SQL Server 2014 で廃止された機能](../discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)   
 [カスタム レポート アイテム](../custom-report-items/custom-report-items.md)   
 [レポート サーバー データベースのアップグレード](upgrade-a-report-server-database.md)  
  
  
