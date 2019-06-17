---
title: SharePoint 2013 への PowerPivot の移行 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: f698ceb1-d53e-4717-a3a0-225b346760d0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6cbbe9f2ba24773ef2b55444e65ce946b0763a41
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66079847"
---
# <a name="migrate-powerpivot-to-sharepoint-2013"></a>SharePoint 2013 への PowerPivot の移行
  
  
 SharePoint 2013 では、インプレース アップグレードはサポートされていません。 ただし、 **データベース接続アップグレードの手順はサポートされています**。 インプレース アップグレードとデータベース アタッチ アップグレードの 2 つの基本的なアップグレード方法をユーザーが選択できた SharePoint 2010 へのアップグレードとは動作が異なります。  
  
 SharePoint 2010 と統合された [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] のインストールを使用している場合は、SharePoint サーバーのインプレース アップグレードを行うことはできません。 ただし、SharePoint 2010 ファームから SharePoint 2013 ファームにコンテンツ データベースとサービス アプリケーション データベースを移行することは可能です。 このトピックでは、データベース アタッチ アップグレードを完了し、PowerPivot に関連する移行を完了するために必要な手順の概要について説明します。  
  
 **[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2013  
  
### <a name="migration-overview"></a>移行の概要  
  
|1|2|3|4|  
|-------|-------|-------|-------|  
|SharePoint 2013 ファームを準備する|データベースをバックアップ、コピー、および復元する|コンテンツ データベースをマウントする|[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] のスケジュールを移行する|  
||[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|SharePoint サーバーの全体管理<br /><br /> Windows PowerShell|SharePoint アプリケーション ページ<br /><br /> Windows PowerShell|  
  
 **このトピックの内容:**  
  
-   [1) SharePoint 2013 ファームを準備する](#bkmk_prepare_sharepoint2013)  
  
-   [2) データベースをバックアップ、コピー、および復元する](#bkmk_backup_restore)  
  
-   [3) Web アプリケーションを準備して、コンテンツ データベースをマウントする](#bkmk_prepare_mount_databases)  
  
-   [4) PowerPivot のスケジュールをアップグレードします。](#bkmk_upgrade_powerpivot_schedules)  
  
-   [その他のリソース](#bkmk_additional_resources)  
  
##  <a name="bkmk_prepare_sharepoint2013"></a> 1) SharePoint 2013 ファームを準備する  
  
1.  > [!TIP]  
    >  既存の Web アプリケーション用に構成されている認証方法を確認します。 SharePoint 2013 Web アプリケーションの既定値は、要求ベースの認証です。 クラシック モード認証用に構成された SharePoint 2010 Web アプリケーションでは、SharePoint 2010 から SharePoint 2013 にデータベースを移行する追加の手順が必要です。 Web アプリケーションがクラシック モード認証用に構成されている場合は、SharePoint 2013 のドキュメントを確認してください。  
  
2.  新しい SharePoint Server 2013 ファームをインストールします。  
  
3.  [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーのインスタンスを SharePoint モードでインストールします。 詳しくは、「 [PowerPivot for SharePoint 2013 Installation](../../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)」をご覧ください。  
  
4.  SharePoint ファーム内の各サーバーで [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013 のインストール パッケージ **spPowerPivot.msi** を実行します。 詳細については、次を参照してください。[インストールまたは PowerPivot を SharePoint アドインのアンインストール&#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)します。  
  
5.  SharePoint 2013 サーバーの全体管理で、前の手順で作成した SharePoint モードの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーを使用するように Excel Services サービス アプリケーションを構成します。 詳細については、の基本的な Analysis Services SharePoint 統合の構成」セクションを参照してください。 [PowerPivot for SharePoint 2013 インストール](../../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)します。  
  
##  <a name="bkmk_backup_restore"></a> 2) データベースをバックアップ、コピー、および復元する  
 「SharePoint データベース アタッチ アップグレード」プロセスは、バックアップする手順のシーケンスと、関連コンテンツをコピー、および復元の PowerPivot サービス アプリケーション データベースを SharePoint 2013 ファーム。  
  
1.  **データベースは、読み取り専用に設定します。** [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]データベース名を右クリックし、クリックして**プロパティ**します。 **[オプション]** ページで、 **[読み取り専用データベース]** プロパティを **[True]** に設定します。  
  
2.  **バックアップ：** 各コンテンツ データベースと SharePoint 2013 ファームに移行するサービス アプリケーション データベースをバックアップします。 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で、データベース名を右クリックし、 **[タスク]** 、 **[バックアップ]** を順にクリックします。  
  
3.  データベース バックアップ ファイル (.bak) をバックアップ先サーバーにファイル コピーします。  
  
4.  **復元します。** 先にデータベースを復元[!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]します。 この手順は、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]を使用して行うことができます。  
  
5.  **データベースを読み取り/書き込みに設定します。** 設定、**読み取り専用データベース**に**False**します。  
  
##  <a name="bkmk_prepare_mount_databases"></a> 3) Web アプリケーションを準備して、コンテンツ データベースをマウントする  
 次の手順の詳細については、次を参照してください。 [SharePoint 2010 から SharePoint 2013 にデータベースをアップグレード](https://go.microsoft.com/fwlink/p/?LinkId=256690)(https://go.microsoft.com/fwlink/p/?LinkId=256690) します。  
  
1.  **データベースをオフラインにする**  
  
     SharePoint サーバーの全体管理を使用して、SharePoint 2013 の各コンテンツ データベースをオフラインにします。 コンテンツ データベースを、コピーしたデータベースに置き換えます。 使用環境にとってどのシーケンスが最適かを検討してください。 次のコンテンツ データベースをオフラインにする前に、各データベースをオフラインにして、関連する置換データベースをマウントすることを検討します。 もう 1 つの方法として、すべてのコンテンツ データベースをグループとしてオフラインにします。  
  
    1.  SharePoint サーバーの全体管理で、 **[アプリケーション構成の管理]** をクリックします。  
  
    2.  **[コンテンツ データベースの管理]** をクリックします。  
  
    3.  データベース名をクリックします。  
  
    4.  **[コンテンツ データベース設定の管理]** で、 **[データベースの状態]** を **[オフライン]** に設定します。  
  
    5.  **[コンテンツ データベースの削除]** を選択します。 コンテンツ データベースに格納されているサイトにアクセスできなくなるという警告に注意してください。  
  
-   **コンテンツ データベースをマウントする:**  
  
     移行したコンテンツ データベースをマウントするには、SharePoint 2013 管理シェルで PowerShell コマンドレットを使用します。 マウントする必要があるのはコンテンツ データベースのみで、サービス アプリケーション データベースをマウントする必要はありません。![PowerShell 関連コンテンツ](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")  
  
    ```  
    Mount-SPContentDatabase "SharePoint_Content_O14-KJSP1" -DatabaseServer "[server name]\powerpivot" -WebApplication [web application URL]  
    ```  
  
     詳細については、次を参照してください。[アタッチまたはデタッチ コンテンツ データベース (SharePoint Server 2010)](https://technet.microsoft.com/library/ff628582.aspx) (https://technet.microsoft.com/library/ff628582.aspx) します。  
  
     **ステップの完了時の状態:** マウント操作が完了したら、ユーザーは、古いコンテンツ データベースに含まれていたファイルを確認できます。 そのため、ユーザーはドキュメント ライブラリのブックを表示して開くことができます。  
  
    > [!TIP]  
    >  移行したブックの新しいスケジュールは、移行プロセスのこの時点で作成することができます。 ただし、スケジュールは、前の SharePoint ファームからコピーしたデータベースではなく、新しい [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] サービス アプリケーション データベースで作成されるため、 古いスケジュールは含められません。 前のデータベースを使用して古いスケジュールを移行する次の手順を完了すると、新しいスケジュールは使用できなくなります。  
  
### <a name="troubleshoot-issues-when-you-attempt-to-mount-databases"></a>データベースをマウントしようとすると発生する問題のトラブルシューティング  
 ここでは、データベースをマウントするときに発生する可能性のある問題についてまとめます。  
  
1.  **認証エラー:** 認証に関連するエラーを表示する場合は、元の web アプリケーションを使用して認証モードを確認します。 エラーは、SharePoint 2013 と SharePoint 2010 の Web アプリケーション間の認証の不一致によって発生する可能性があります。 詳細については、「 [1) SharePoint 2013 ファームを準備する](#bkmk_prepare_sharepoint2013) 」を参照してください。  
  
2.  **不足。** PowerPivot の .dll の不足に関連するエラーが発生する場合、 **spPowerPivot.msi**がインストールされていない、または[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]PowerPivot を構成する構成ツールが使用されていません。  
  
##  <a name="bkmk_upgrade_powerpivot_schedules"></a> 4) PowerPivot のスケジュールをアップグレードします。  
 ここでは、PowerPivot のスケジュールの移行に関する詳細とオプションについて説明します。 スケジュールを移行するには、2 つの手順を実行します。 まず、移行したサービス アプリケーション データベースを使用するように PowerPivot サービス アプリケーションを構成し、 次に、スケジュールを移行する 2 つの方法のうちいずれかを選択します。  
  
 **移行したサービス アプリケーション データベースを使用するようにサービス アプリケーションを構成する**  
  
 SharePoint サーバーの全体管理で、コピーした前のサービス アプリケーション データベースを使用するように PowerPivot サービス アプリケーションを構成します。 PowerPivot サービスによって、サービス アプリケーション データベースが新しいスキーマにアップグレードされます。  
  
1.  SharePoint サーバーの全体管理で **[サービス アプリケーションの管理]** をクリックします。  
  
2.  PowerPivot サービス アプリケーション、たとえば「既定の PowerPivot サービス アプリケーション」をクリックして、サービス アプリケーションの名前を検索し、をクリックして**プロパティ**SharePoint リボンでします。  
  
3.  データベース サーバーの名前付きインスタンスとデータベース名を、 バックアップ、コピー、および復元したデータベースの正しい名前に更新します。 **[OK]** をクリックすると、サービス アプリケーション データベースがアップグレードされます。 エラーは ULS ログに格納されます。  
  
 **PowerPivot のスケジュールをアップグレードします。**  
  
 更新スケジュールを移行するには、PowerPivot サービス アプリケーションを構成します。  
  
-   **移行するスケジュールのオプション 1。SharePoint ファームの管理者**  
  
    1.  SharePoint 2013 の管理の実行で、`Set-PowerPivotServiceApplication`コマンドレットと、`-StartMigratingRefreshSchedules`必要に応じてスケジュールを移行に自動で有効にするスイッチ![PowerShell 関連コンテンツ](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell 関連コンテンツ"). 次の Windows PowerShell スクリプトは、PowerPivot サービス アプリケーションが 1 つだけであることを前提としています。  
  
        ```  
        $app=Get-PowerPivotServiceApplication  
        Set-PowerPivotServiceApplication $app -StartMigratingRefreshSchedules  
        ```  
  
         この Windows PowerShell スクリプトを実行すると、スケジュールがアクティブになり、次回の適切なタイミングで実行されるようになります。 ただし、定期更新ページ上の状態は有効になりません。 スケジュールは初めて実行するときに移行され、定期更新ページで **[有効]**  が [True] に変わります。  
  
    2.  StartMigratingRefreshSchedules プロパティの現在値を確認する場合は、次の PowerShell スクリプトを実行します。 このスクリプトは、すべての PowerPivot サービス アプリケーション オブジェクトをループし、名前とプロパティ値を表示します。  
  
        ```  
        $apps = Get-PowerPivotServiceApplication  
        foreach ($app in $apps){}  
        Get-PowerPivotServiceApplication $appp | format-table -property displayname,id,StartMigratingRefreshSchedules  
        ```  
  
     **移行のスケジュールするオプション 2。ユーザーが各ブックを更新します。**  
  
    1.  スケジュールを移行するもう 1 つの方法は、ブックごとに定期更新を有効にすることです。 ブックがあるドキュメント ライブラリに移動します。  
  
    2.  ショートカット メニューを開き、 **[PowerPivot のデータ更新の管理]** をクリックします。  
  
    3.  **[定期更新]** セクションで、 **[有効化]** をクリックします。  
  
    4.  **[さらに、できるだけ早く更新を行います]** を選択できます。 このオプションでは、[OK] をクリックするとすぐに更新のインスタンスが 1 つキューに追加されます。 通常の更新スケジュールも適切な時間にトリガーされます。  
  
    5.  **[OK]** をクリックします。 これで、更新ページに更新履歴が表示されるようになり、スケジュールは通常の時間に実行されます。  
  
 **SQL Server 2008 R2 PowerPivot ブック**  
  
-   SQL Server 2008 R2 PowerPivot ブックを SQL Server 2012 SP1 PowerPivot for SharePoint 2013 で使用している場合は、自動的にはアップグレードされません。 2008 R2 ブックが格納されたコンテンツ データベースを移行すると、ブックを使用できるようにはなりますが、スケジュールはアップグレードされません。  
  
-   詳細については、「 [ブックのアップグレードと定期データ更新 &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)」を参照してください。  
  
##  <a name="bkmk_additional_resources"></a> その他のリソース  
  
> [!NOTE]  
>  [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] および SharePoint データベース アタッチ アップグレードの詳細については、以下を参照してください。  
  
-   [ブックのアップグレードと定期データ更新 &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
-   [SharePoint 2013 へのアップグレード プロセスの概要](https://go.microsoft.com/fwlink/p/?LinkId=256688)(https://go.microsoft.com/fwlink/p/?LinkId=256688) します。  
  
-   [SharePoint 2013 へアップグレードする前に環境をクリーンアップする](https://go.microsoft.com/fwlink/p/?LinkId=256689)(https://go.microsoft.com/fwlink/p/?LinkId=256689) します。  
  
-   [SharePoint 2010 から SharePoint 2013 までデータベースをアップグレード](https://go.microsoft.com/fwlink/p/?LinkId=256690)(https://go.microsoft.com/fwlink/p/?LinkId=256690) します。  
  
  
