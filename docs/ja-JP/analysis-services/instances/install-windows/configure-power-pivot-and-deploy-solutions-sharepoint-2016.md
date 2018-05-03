---
title: Power Pivot の構成し、ソリューションの配置 (SharePoint 2016) |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ppvt-sharepoint
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 384f1fdec5b77dcc980954e72fe5bfa07f617601
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="configure-power-pivot-and-deploy-solutions-sharepoint-2016"></a>Power Pivot の構成とソリューションの配置 (SharePoint 2016)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  このトピックでは、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ギャラリー、定期データ更新、管理ダッシュボード、データ プロバイダーといった [!INCLUDE[SPS2016](../../../includes/sps2016-md.md)] の [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 機能に対する中間層機能強化の配置および構成について説明します。 **[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2016 構成** ツールを実行して、以下の操作を完了します。  
  
-   SharePoint ソリューション ファイルを配置する。  
  
-   [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] サービス アプリケーションを作成する。  
  
-   バックエンド サービスと、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] モードの [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] サーバーをインストールする方法の詳細については、「 [Power Pivot モードでの Analysis Services のインストール](../../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)」を参照してください。  
  
 インストール方法について、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] SharePoint 2016 構成ツールでは、次を参照してください。[インストールまたは for SharePoint アドイン (SharePoint 2016) Power Pivot をアンインストール](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2016.md)です。  
  
##  <a name="bkmk_run_configuration_tool"></a> Power Pivot for SharePoint 2016 の構成の実行  
 **注:** 次の手順を実行するには、ファーム管理者である必要があります。 次のようなエラー メッセージが表示される場合があります。  
  
-   "ユーザーはファームの管理者ではありません。 検証エラーを修正して、再試行してください。"  
  
 SharePoint のインストール時に使用したアカウントでログインするか、SharePoint サーバーの全体管理サイトのプライマリ管理者としてセットアップ アカウントを構成します。  
  
1.  **[スタート]** メニューの **[すべてのプログラム]** をポイントし、[ [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]]、 **[構成ツール]**、 **[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2016 の構成**の順にクリックします。 ツールは、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint がローカル サーバーにインストールされている場合にのみ表示されます。  
  
2.  **[[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint の構成または修復]** をクリックして、**[OK]** をクリックします。  
  
3.  このツールでは、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] の現在の状態と構成を完了するために必要な手順を確認するための検証が実行されます。 ウィンドウを最大化します。 ウィンドウの下部に **[検証]**、 **[実行]**、および **[終了]** の各コマンドを含むボタン バーが表示されます。  
  
4.  **[パラメーター]** タブで、次の操作を行います。  
  
    1.  **[既定のアカウント ユーザー名]:** 既定のアカウントのドメイン ユーザー アカウントを入力します。 このアカウントは、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] サービス アプリケーション プールなどのサービスを準備する際に使用されます。 Network Service や Local System などのビルトイン アカウントは指定しないでください。 ビルトイン アカウントを指定する構成はブロックされます。  
  
    2.  **[データベース サーバー]:** SharePoint ファームでサポートされている SQL Server データベース エンジンを使用できます。  
  
    3.  **[パスフレーズ]:** パスフレーズを入力します。 新しい SharePoint ファームを作成する場合、SharePoint ファームにサーバーまたはアプリケーションを追加するたびにこのパスフレーズが使用されます。 ファームが既に存在する場合、ファームにサーバー アプリケーションを追加するためのパスフレーズを入力してください。  
  
    4.  左側のウィンドウで **[サイト コレクションの作成]** をクリックします。 **[サイトの URL]** をメモしておくと、この後の手順で参照できます。 SharePoint サーバーがまだ構成されていない場合、構成ウィザードでは Web アプリケーションとサイト コレクション URL のルートは既定で `http://[ServerName]`になります。 既定値を変更するには、左側のウィンドウの **[既定の Web アプリケーションの作成]** ページおよび **[Web アプリケーション ソリューションの配置]** ページを確認します。  
  
5.  必要に応じて、各アクションを完了するために使用された残りの入力値を確認します。 左側のウィンドウで各アクションをクリックして、アクションの詳細を確認します。 各アクションの詳細については、このトピックの [「Power Pivot for SharePoint 2010 の構成または修復 (Power Pivot 構成ツール)](http://msdn.microsoft.com/en-us/d61f49c5-efaa-4455-98f2-8c293fa50046) 」で「サーバーの構成に使用する入力値」セクションを参照してください。  
  
6.  必要に応じて、今回は処理しないすべてのアクションを削除します。 たとえば、Secure Store Service を後で構成する場合は、 **[Secure Store Service の構成]** を選択し、 **[この操作をタスク一覧に含めます]** チェック ボックスをオフにします。  
  
7.  **[検証]** をクリックして、ツールで一覧のアクションを処理するための十分な情報があるかどうかを確認します。 検証エラーがある場合は、左ペインで警告をクリックして検証エラーの詳細を確認します。 検証エラーを修正し、もう一度 **[検証]** をクリックします。  
  
8.  **[実行]** をクリックして、タスク一覧にあるすべてのアクションを処理します。 **[実行]** は、アクションの検証後に有効になります。 **[実行]** が有効になっていない場合は、まず **[検証]** をクリックしてください。  
  
 詳細については、「 [Power Pivot for SharePoint 2010 の構成または修復 (Power Pivot 構成ツール)](http://msdn.microsoft.com/en-us/d61f49c5-efaa-4455-98f2-8c293fa50046)」を参照してください。  
  
##  <a name="bkmk_verify_powerpivot"></a> Power Pivot の構成の確認  
 **サービス**  
  
1.  サーバーの全体管理で、[システム設定] の **[サーバーのサービスの管理]** を選択します。  
  
2.  **SQL Server [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] システム サービス**が開始されていることを確認します。  
  
 **ファーム機能**  
  
1.  サーバーの全体管理で、[システム設定] の **[ファーム機能の管理]** を選択します。  
  
2.  **[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 統合機能** が **[アクティブ]** になっていることを確認します。  
  
 **サイト コレクション機能**  
  
1.  構成ツールによって作成されたサイトの URL を参照します。  
  
     選択**設定**![SharePoint 設定](../../../analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 設定")、順にクリック**サイト設定**です。  
  
     **[サイト コレクションの機能]** をクリックします。  
  
2.  **[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 機能の統合** が **[アクティブ]** になっていることを確認します。  
  
 **[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] サービス アプリケーション:**  
  
1.  サーバーの全体管理で、 **[アプリケーション構成の管理]** の **[サービス アプリケーションの管理]** を選択します。  
  
2.  サービス アプリケーションの状態が **[開始済み]** になっていることを確認します。 既定の名前は、**[既定の [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] サービス アプリケーション]** です。  
  
     サービス アプリケーションの名前を選択して、このサービス アプリケーションの [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 管理ダッシュボードを開きます。 最初に使用するときは、ダッシュボードの読み込みに数分かかります。  
  
 詳細については、「 [Verify a Power Pivot for SharePoint Installation](../../../analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation.md)」を参照してください。  
  
##  <a name="bkmk_troubleshoot_issues"></a> 問題のトラブルシューティング  
 問題のトラブルシューティングに役立てるために、診断ログを有効にすることをお勧めします。  
  
1.  SharePoint サーバーの全体管理で、 **[監視]** をクリックし、 **[使用状況と正常性のデータ収集の構成]** を選択します。  
  
2.  **[使用状況データ収集を有効にする]** チェック ボックスがオンになっていることを確認します。  
  
3.  次のイベントが選択されていることを確認します。  
  
    -   学歴利用統計情報の使用状況フィールドの定義  
  
    -   [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 接続  
  
    -   [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 読み込みデータの使用状況  
  
    -   [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] クエリの使用状況  
  
    -   [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] アンロード データの使用状況  
  
4.  **[正常性データの収集を有効にする]** が選択されていることを確認します。  
  
5.  **[OK]** を選択します。  
  
 更新のデータのトラブルシューティングに関する詳細については、次を参照してください。 [Power Pivot データ更新のトラブルシューティング](http://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx)(http://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx)です。  
  
 構成ツールの詳細については、「 [Power Pivot Configuration Tools](../../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md)」を参照してください。  
  
  
