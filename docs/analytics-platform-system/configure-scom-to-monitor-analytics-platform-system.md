---
title: Analytics Platform System を監視するための SCOM の構成 |Microsoft Docs
description: Analytics Platform System の System Center Operations Manager (SCOM) 管理パックを構成するこれらの手順に従います。 管理パックは、SCOM から Analytics Platform System を監視する必要があります。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 5ec495b3dd321f712aed54fb3b337efe85719be5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961234"
---
# <a name="configure-system-center-operations-manager-scom-to-monitor-analytics-platform-system"></a>System Center Operations Manager (SCOM) Analytics Platform System を監視するための構成します。
Analytics Platform System の System Center Operations Manager (SCOM) 管理パックを構成するこれらの手順に従います。 管理パックは、SCOM から Analytics Platform System を監視する必要があります。  
  
## <a name="BeforeBegin"></a>はじめに  
**前提条件**  
  
System Center Operations Manager 2007 R2 は、インストールして実行する必要があります。  
  
管理パックをインストールして構成する必要があります。 参照してください[SCOM 管理パックをインストール&#40;Analytics Platform System&#41; ](install-the-scom-management-packs.md)と[PDW 用の SCOM 管理パックをインポート&#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-pdw.md)します。  
  
## <a name="ConfigureRunAsProfile"></a>System Center でのユーザーとして実行プロファイルを構成します。  
System Center を設定するには、次の手順を実行しなければなりません。  
  
-   実行アカウントを作成、 **AP Watcher**ドメイン ユーザーにマップし、 **AP ウォッチャーの Microsoft アカウント。**  
  
-   実行アカウントを作成、 **monitoring_user** AP ユーザーにマップし、 **Microsoft AP のアクション アカウント**します。  
  
タスクを実行する方法の詳細な手順を次に示します。  
  
1.  作成、 **AP Watcher**持つ実行アカウント**Windows**アカウントの種類の**AP Watcher**ドメイン ユーザー。  
  
    1.  移動します、**管理**ウィンドウで右クリックで**実行構成** -> **アカウント**選択**実行アカウントの作成.**  
  
        ![ConfigureScomCreateRunAsAccount](./media/configure-scom-to-monitor-analytics-platform-system/ConfigureScomCreateRunAsAccount.png "ConfigureScomCreateRunAsAccount")  
  
    2.  **作成実行アカウント ウィザード**ダイアログ ボックスが開きます。 **[はじめに]** ページで **[次へ]** をクリックします。  
  
    3.  **全般プロパティ**] ページで、[ **Windows**から**実行アカウントの種類**として「AP ウォッチャー」を指定し、**表示名**します。  
  
        ![CreateRunAsAccountWizardGeneralProperties](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties.png "CreateRunAsAccountWizardGeneralProperties")  
  
    4.  **資格情報** ページで、 ![CreateRunAsAccountWizardCredentials](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials.png "CreateRunAsAccountWizardCredentials")  
  
    5.  **配布セキュリティ** ページで、**安全性の低い** をクリックし、**作成**ボタン 完了 をクリックします。  
  
        ![CreateRunAsAccountWizardDistributionSecurity](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardDistributionSecurity.png "CreateRunAsAccountWizardDistributionSecurity")  
  
        1.  使用する場合、**より安全な**オプション、資格情報の配布先コンピューターを手動で指定する必要があります。 これを行うには、実行アカウントを作成した後を右クリックし、選択**プロパティ**します。  
  
        2.  移動し、**配布** タブと**追加**コンピューターが必要な。  
  
            ![RunAsAccountProperties](./media/configure-scom-to-monitor-analytics-platform-system/RunAsAccountProperties.png "RunAsAccountProperties")  
  
2.  設定、 **AP ウォッチャーの Microsoft アカウント**を使用するプロファイル**AP Watcher**アカウントとして実行します。  
  
    1.  移動します**管理** -> **構成として実行** -> **プロファイル**します。  
  
        ![AdministrationRunAsConfigurationProfiles](./media/configure-scom-to-monitor-analytics-platform-system/AdministrationRunAsConfigurationProfiles.png "AdministrationRunAsConfigurationProfiles")  
  
    2.  右クリックして**Microsoft AP 監視アカウント**クリックし、一覧から**プロパティ**します。  
  
        ![MicrosoftApsWatcherAccountProperties](./media/configure-scom-to-monitor-analytics-platform-system/MicrosoftApsWatcherAccountProperties.png "MicrosoftApsWatcherAccountProperties")  
  
    3.  **実行プロファイル ウィザード**ダイアログ ボックスが開きます。 Skip、**概要**をクリックしてページ**次**します。  
  
    4.  **全般プロパティ**] ページで [**次**します。  
  
    5.  **アカウントとして実行** ページで、をクリックして、**追加しています.** ボタンをクリックし、以前に作成した選択**AP Watcher**アカウントとして実行します。  
  
        ![RunAsProfileWizardAdd](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd.png "RunAsProfileWizardAdd")  
  
    6.  クリックして**保存**プロファイルの割り当てを完了します。  
  
3.  APS アプライアンスの検出が完了するまでに待機します。  
  
    1.  移動し、**監視**ウィンドウを開きます、 **SQL Server アプライアンス** -> **Microsoft Analytics Platform System**  ->  **アプライアンス**状態ビュー。  
  
        ![SqlServerApplianceMicrosoftApsAppliances](./media/configure-scom-to-monitor-analytics-platform-system/SqlServerApplianceMicrosoftApsAppliances.png "SqlServerApplianceMicrosoftApsAppliances")  
  
    2.  アプライアンスが一覧に表示されるまで待ちます。 アプライアンスの名前は、レジストリで指定されたいずれかになければなりません。 検出が完了したら、一覧表示されますが、監視されていないすべてのアプライアンスが表示されます。 監視を有効にするには、次の手順に従います。  
  
    > [!NOTE]  
    > アプライアンスの初期検出が完了するを待機しているときに、次の手順を同時に実行することができます。  
  
4.  もう 1 つ新しい実行アカウントを正常性データの取得の AP をクエリを作成します。  
  
    1.  手順 1 の説明に従って新しい実行アカウントの作成を開始します。  
  
    2.  **全般プロパティ**] ページで、[**基本認証**アカウントの種類。  
  
        ![CreateRunAsAccountWizardGeneralProperties2](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties2.png "CreateRunAsAccountWizardGeneralProperties2")  
  
    3.  **資格情報** ページで、AP 正常性状態の Dmv にアクセスする有効な資格情報を指定します。  
  
        ![CreateRunAsAccountWizardCredentials2](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials2.png "CreateRunAsAccountWizardCredentials2")  
  
5.  構成、 **Microsoft AP のアクション アカウント**AP インスタンスの新しく作成された実行アカウントを使用するプロファイル。  
  
    1.  移動し、 **Microsoft AP のアクション アカウント**ように手順 2. で説明されているプロパティ。  
  
    2.  **アカウントとして実行**] ページで [**追加しています.** と 
    3.  新しく作成された実行アカウントを選択します。  
  
        ![RunAsProfileWizardAdd2](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd2.png "RunAsProfileWizardAdd2")  
  
## <a name="next-step"></a>次の手順  
できたので、管理パックを構成しているアプライアンスの監視を開始する準備が整いました。 詳細については、次を参照してください。 [System Center Operations Manager を使用して、アプライアンスの監視&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)します。  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
