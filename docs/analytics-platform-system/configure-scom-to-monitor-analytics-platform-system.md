---
title: Analytics Platform System を監視する SCOM の構成 |Microsoft ドキュメント
description: Analytics Platform System の System Center Operations Manager (SCOM) 管理パックを構成するこれらの手順に従います。 SCOM から分析プラットフォーム システムを監視する管理パックが必要です。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 4c2e8a42d488c18e705c9d7d8c1d53c9ff7c9cb8
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="configure-system-center-operations-manager-scom-to-monitor-analytics-platform-system"></a>System Center Operations Manager (SCOM) を分析プラットフォーム システムの監視を構成します。
Analytics Platform System の System Center Operations Manager (SCOM) 管理パックを構成するこれらの手順に従います。 SCOM から分析プラットフォーム システムを監視する管理パックが必要です。  
  
## <a name="BeforeBegin"></a>はじめに  
**前提条件**  
  
System Center Operations Manager 2007 R2 は、インストールして実行する必要があります。  
  
管理パックをインストールして構成する必要があります。 参照してください[SCOM 管理パックをインストール&#40;Analytics Platform System&#41; ](install-the-scom-management-packs.md)と[PDW の SCOM 管理パックをインポート&#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-pdw.md)です。  
  
## <a name="ConfigureRunAsProfile"></a>System Center でのユーザーとして実行プロファイルを構成します。  
System Center を構成するのには、次の手順を実行する必要が。  
  
-   実行アカウントを作成、 **APS ウォッチャー**ドメイン ユーザーにマップ、 **Microsoft APS 監視アカウント。**  
  
-   実行アカウントを作成、 **monitoring_user** APS ユーザーにマップし、 **Microsoft APS アクション アカウント**です。  
  
タスクを実行する方法の詳細な手順を次に示します。  
  
1.  作成、 **APS ウォッチャー**実行アカウントを**Windows**アカウントのタイプ、 **APS ウォッチャー**ドメイン ユーザー。  
  
    1.  移動、**管理**ペインで右クリック**実行構成** -> **アカウント**を選択し、**実行アカウントを作成しています.**  
  
        ![ConfigureScomCreateRunAsAccount](./media/configure-scom-to-monitor-analytics-platform-system/ConfigureScomCreateRunAsAccount.png "ConfigureScomCreateRunAsAccount")  
  
    2.  **作成する実行アカウント ウィザード**ダイアログが開きます。 **概要** ページで、をクリックして**次**です。  
  
    3.  **全般プロパティ**] ページで、[ **Windows**から**実行アカウントの種類**として「APS ウォッチャー」を指定し、**表示名**です。  
  
        ![CreateRunAsAccountWizardGeneralProperties](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties.png "CreateRunAsAccountWizardGeneralProperties")  
  
    4.  **資格情報** ページで、 ![CreateRunAsAccountWizardCredentials](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials.png "CreateRunAsAccountWizardCredentials")  
  
    5.  **配布セキュリティ** ページで、**安全性の低い** をクリックし、**作成**完了 をクリックします。  
  
        ![CreateRunAsAccountWizardDistributionSecurity](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardDistributionSecurity.png "CreateRunAsAccountWizardDistributionSecurity")  
  
        1.  使用する場合、**より安全な**オプション、資格情報の配布先コンピューターを手動で指定する必要があります。 これを行うには、実行アカウントを作成した後を右クリックし、選択**プロパティ**です。  
  
        2.  移動、**配布** タブと**追加**コンピューターが必要です。  
  
            ![RunAsAccountProperties](./media/configure-scom-to-monitor-analytics-platform-system/RunAsAccountProperties.png "RunAsAccountProperties")  
  
2.  設定、 **Microsoft APS 監視アカウント**を使用するプロファイル**APS ウォッチャー**アカウントとして実行します。  
  
    1.  移動**管理** -> **実行構成** -> **プロファイル**です。  
  
        ![AdministrationRunAsConfigurationProfiles](./media/configure-scom-to-monitor-analytics-platform-system/AdministrationRunAsConfigurationProfiles.png "AdministrationRunAsConfigurationProfiles")  
  
    2.  右クリックして**Microsoft APS 監視アカウント**クリックし、一覧から**プロパティ**です。  
  
        ![MicrosoftApsWatcherAccountProperties](./media/configure-scom-to-monitor-analytics-platform-system/MicrosoftApsWatcherAccountProperties.png "MicrosoftApsWatcherAccountProperties")  
  
    3.  **実行プロファイル ウィザード**ダイアログが開きます。 Skip、**概要**をクリックしてページ**次**です。  
  
    4.  **全般プロパティ** ページで、をクリックして**次**です。  
  
    5.  **アカウントとして実行** ページで、をクリックして、**追加しています.** ボタンをクリックし、以前に作成した選択**APS ウォッチャー**アカウントとして実行します。  
  
        ![RunAsProfileWizardAdd](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd.png "RunAsProfileWizardAdd")  
  
    6.  をクリックして**保存**プロファイルの割り当てを完了します。  
  
3.  APS アプライアンスの検出を完了するまで待機します。  
  
    1.  移動し、**監視**ウィンドウ、開く、 **SQL Server アプライアンス** -> **Microsoft Analytics Platform System**  ->  **アプライアンス**状態ビュー。  
  
        ![SqlServerApplianceMicrosoftApsAppliances](./media/configure-scom-to-monitor-analytics-platform-system/SqlServerApplianceMicrosoftApsAppliances.png "SqlServerApplianceMicrosoftApsAppliances")  
  
    2.  アプライアンスが一覧に表示されるまで待ちます。 アプライアンスの名前は、レジストリで指定された 1 つに一致する必要があります。 探索の完了後に表示されますが、監視されていないすべてのアプライアンスが表示されます。 監視できるように、次の手順に従います。  
  
    > [!NOTE]  
    > アプライアンスが初期検出が終了するを待機しているときに、次の手順を同時に実行することができます。  
  
4.  新しいユーザーとして実行する別のアカウント クエリ AP の正常性データの取得を作成します。  
  
    1.  手順 1 の説明に従って、新しい実行アカウントの作成を開始します。  
  
    2.  **全般プロパティ**] ページで、[**基本認証**アカウントの種類。  
  
        ![CreateRunAsAccountWizardGeneralProperties2](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties2.png "CreateRunAsAccountWizardGeneralProperties2")  
  
    3.  **資格情報** ページで、AP 正常性状態の Dmv にアクセスする有効な資格情報を指定します。  
  
        ![CreateRunAsAccountWizardCredentials2](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials2.png "CreateRunAsAccountWizardCredentials2")  
  
5.  構成、 **Microsoft APS アクション アカウント**APS インスタンスに、新しく作成された実行アカウントを使用するプロファイル。  
  
    1.  移動し、 **Microsoft APS アクション アカウント**ように手順 2. で説明されているプロパティ。  
  
    2.  **アカウントとして実行**] ページで [**追加しています.** 」、「 
    3.  新しく作成された実行アカウントを選択します。  
  
        ![RunAsProfileWizardAdd2](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd2.png "RunAsProfileWizardAdd2")  
  
## <a name="next-step"></a>次の手順  
管理パックを構成したら、これでは、アプライアンスの監視を開始する準備ができたらです。 詳細については、次を参照してください。 [System Center Operations Manager を使用してアプライアンスをモニター &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)です。  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
