---
title: PowerPivot の構成とソリューションの配置 (SharePoint 2013) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6401fd92-f43b-450e-8298-12db644c25bc
author: minewiskan
ms.author: owend
ms.openlocfilehash: e26faf2ef80f416858665893e14e405eab7254d6
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84543904"
---
# <a name="configure-powerpivot-and-deploy-solutions-sharepoint-2013"></a>PowerPivot の構成とソリューションの配置 (SharePoint 2013)
  このトピックでは、PowerPivot ギャラリー、定期データ更新、管理ダッシュボード、データ プロバイダーなどの [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] の PowerPivot 機能への中間層機能強化の展開および構成について説明します。 **PowerPivot for SharePoint 2013 の構成** ツールを実行して、以下を完了します。  
  
-   SharePoint ソリューション ファイルを配置する。  
  
-   PowerPivot サービス アプリケーションを作成する。  
  
-   Excel Services アプリケーションが SharePoint モードの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーを使用するように構成する。 バックエンドサービスと、SharePoint モードでのサーバーのインストールの詳細につい [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ては、「 [PowerPivot for SharePoint 2013 のインストール](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)」を参照してください。  
  
 PowerPivot for SharePoint 2013 構成ツールのインストールの詳細については、「 [SharePoint 2013 &#40;PowerPivot for SharePoint アドインをインストールまたはアンインストール](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)する」を参照してください&#41;  
  
 このトピックは、次のセクションで構成されています。  
  
 [PowerPivot for SharePoint 2013 の構成の実行](#bkmk_run_configuration_tool)  
  
 [PowerPivot の構成の確認](#bkmk_verify_powerpivot)  
  
 [問題のトラブルシューティング](#bkmk_troubleshoot_issues)  
  
##  <a name="run-powerpivot-for-sharepoint-2013-configuration"></a><a name="bkmk_run_configuration_tool"></a>PowerPivot for SharePoint 2013 構成の実行  
 **注:**[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] セットアップ ウィザードでは、 [!INCLUDE[ssGeminiLong](../../../includes/ssgeminilong-md.md)]の 2 種類の構成ツールがインストールされます。 これらのツールはそれぞれ異なるバージョンの SharePoint をサポートします。  
  
|名前|説明|  
|----------|-----------------|  
|PowerPivot for SharePoint 2013 の構成|SharePoint 2013|  
|PowerPivot 構成ツール|SharePoint 2010 Service Pack 1 (SP1)|  
  
 **注:** 次の手順を実行するには、ファーム管理者である必要があります。 次のようなエラー メッセージが表示される場合があります。  
  
-   "ユーザーはファームの管理者ではありません。 検証エラーを修正して、再試行してください。"  
  
 SharePoint のインストール時に使用したアカウントでログインするか、SharePoint サーバーの全体管理サイトのプライマリ管理者としてセットアップ アカウントを構成します。  
  
1.  **[スタート]** メニューの **[すべてのプログラム]** をクリックし、[ [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]] をクリックします。次に、 **[構成ツール]** をクリックし、 **[PowerPivot For SharePoint 2013 の構成]** をクリックします。 ツールは、PowerPivot for SharePoint がローカル サーバーにインストールされている場合にのみ表示されます。  
  
2.  **[PowerPivot for SharePoint の構成または修復]** をクリックし、 **[OK]** をクリックします。  
  
3.  このツールでは、PowerPivot の現在の状態と構成を完了するために必要な手順を確認するための検証が実行されます。 ウィンドウを最大化します。 ウィンドウの下部に **[検証]**、 **[実行]**、および **[終了]** の各コマンドを含むボタン バーが表示されます。  
  
4.  **[パラメーター]** タブで、次の操作を行います。  
  
    1.  **[既定のアカウント ユーザー名]:** 既定のアカウントのドメイン ユーザー アカウントを入力します。 このアカウントは、PowerPivot サービス アプリケーション プールなどのサービスを準備する際に使用します。 Network Service や Local System などのビルトイン アカウントは指定しないでください。 ビルトイン アカウントを指定する構成はブロックされます。  
  
    2.  **[データベース サーバー]:** SharePoint ファームでサポートされている SQL Server データベース エンジンを使用できます。  
  
    3.  **[パスフレーズ]:** パスフレーズを入力します。 新しい SharePoint ファームを作成する場合、SharePoint ファームにサーバーまたはアプリケーションを追加するたびにこのパスフレーズが使用されます。 ファームが既に存在する場合、ファームにサーバー アプリケーションを追加するためのパスフレーズを入力してください。  
  
    4.  **[Excel Services 用 PowerPivot サーバー]:** SharePoint モードの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーの名前を入力します。 シングル サーバー配置では、データベース サーバーと同じサーバーです。 `[ServerName]\powerpivot`  
  
    5.  左側のウィンドウで **[サイト コレクションの作成]** をクリックします。 **[サイトの URL]** をメモしておくと、この後の手順で参照できます。 SharePoint サーバーがまだ構成されていない場合、構成ウィザードでは Web アプリケーションとサイト コレクション URL のルートは既定で `http://[ServerName]`になります。 既定値を変更するには、左側のウィンドウの **[既定の Web アプリケーションの作成]** ページおよび **[Web アプリケーション ソリューションの配置]** ページを確認します。  
  
5.  必要に応じて、各アクションを完了するために使用された残りの入力値を確認します。 左側のウィンドウで各アクションをクリックして、アクションの詳細を確認します。 それぞれの詳細については、このトピックの「 [&#41;&#40;PowerPivot 構成ツールの構成または修復 2010 PowerPivot for SharePoint](../../configure-repair-powerpivot-sharepoint-2010.md)でのサーバーの構成に使用する入力値」を参照してください。  
  
6.  必要に応じて、今回は処理しないすべてのアクションを削除します。 たとえば、Secure Store Service を後で構成する場合は、 **[Secure Store Service の構成]** をクリックし、 **[この操作をタスク一覧に含めます]** チェック ボックスをオフにします。  
  
7.  **[検証]** をクリックして、一覧のアクションを処理するための十分な情報があるかどうかを確認します。 検証エラーがある場合は、左ペインで警告をクリックして検証エラーの詳細を確認します。 検証エラーを修正し、もう一度 **[検証]** をクリックします。  
  
8.  **[実行]** をクリックして、タスクの一覧にあるすべてのアクションを処理します。 **[実行]** は、アクションの検証後に有効になります。 **[実行]** が有効になっていない場合は、まず **[検証]** をクリックしてください。  
  
 詳細については、「 [PowerPivot for SharePoint 2010 &#40;PowerPivot 構成ツールの構成または修復](../../configure-repair-powerpivot-sharepoint-2010.md)」を参照してください&#41;  
  
##  <a name="verify-powerpivot-configuration"></a><a name="bkmk_verify_powerpivot"></a>PowerPivot の構成の確認  
 **サービス**  
  
1.  サーバーの全体管理で、[システム設定] の [**サーバーのサービスの管理**] をクリックします。  
  
2.  **SQL Server Analysis Services** と **SQL Server PowerPivot System サービス** が開始されていることを確認します。  
  
 **ファーム機能**  
  
1.  サーバーの全体管理で、[システム設定] の **[ファーム機能の管理]** をクリックします。  
  
2.  **[PowerPivot 統合機能]** が **[アクティブ]** になっていることを確認します。  
  
 **サイト コレクション機能**  
  
1.  構成ツールによって作成されたサイトの URL を参照します。  
  
     [**設定**] [![SharePoint の設定](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint の設定")] の順にクリックし、[**サイトの設定**] をクリックします。  
  
     **[サイト コレクションの機能]** をクリックします。  
  
2.  **[サイト コレクションの PowerPivot 機能の統合]** が **[アクティブ]** になっていることを確認します。  
  
 **PowerPivot サービスアプリケーション:**  
  
1.  サーバーの全体管理で、 **[アプリケーション構成の管理]** の **[サービス アプリケーションの管理]** をクリックします。  
  
2.  サービス アプリケーションの状態が **[開始済み]** になっていることを確認します。 既定の名前は、"**既定の PowerPivot サービスアプリケーション**" です。  
  
     サービス アプリケーションの名前をクリックして、このサービス アプリケーションの PowerPivot 管理ダッシュボードを開きます。 最初に使用するときは、ダッシュボードの読み込みに数分かかります。  
  
 詳細については、「 [Verify a PowerPivot for SharePoint Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation)」を参照してください。  
  
##  <a name="troubleshoot-issues"></a><a name="bkmk_troubleshoot_issues"></a>問題のトラブルシューティング  
 問題のトラブルシューティングに役立てるために、診断ログを有効にすることをお勧めします。  
  
1.  SharePoint サーバーの全体管理で、 **[監視]** をクリックし、 **[使用状況と正常性のデータ収集の構成]** をクリックします。  
  
2.  **[使用状況データ収集を有効にする]** チェック ボックスがオンになっていることを確認します。  
  
3.  次のイベントが選択されていることを確認します。  
  
    -   学歴利用統計情報の使用状況フィールドの定義  
  
    -   PowerPivot 接続  
  
    -   PowerPivot 読み込みデータの使用状況  
  
    -   PowerPivot クエリの使用状況  
  
    -   PowerPivot アンロード データの使用状況  
  
4.  **[正常性データの収集を有効にする]** が選択されていることを確認します。  
  
5.  **[OK]** をクリックします。  
  
 データ更新のトラブルシューティングの詳細については、「 [PowerPivot データ更新のトラブルシューティング](https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx)」 (を参照してください https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx) 。  
  
 構成ツールの詳細については、「 [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md)」を参照してください。  
  
  
