---
title: データ更新と Windows 認証をサポートしていないデータソースをスケジュールする (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d8d875bc-7823-46b7-a939-867cefd4de12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b4851c8054434713e69d8bf63b046484a01f0398
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66071156"
---
# <a name="schedule-data-refresh-and-data-sources-that-do-not-support-windows-authentication-powerpivot-for-sharepoint"></a>定期データ更新と Windows 認証をサポートしないデータ ソース (PowerPivot for SharePoint)
  このトピックでは、Windows 認証を**サポートしない**データ ソースを使用できる PowerPivot for SharePoint 定期データ更新のワークフローについて説明します。 たとえば、Oracle データ ソースまたは IDM DB2 データ ソースが該当します。 このトピックにある図と手順では、Oracle データ ソースを参照していますが、他のデータ ソースにも同じワークフローが当てはまります。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** Sharepoint 2010 &#124; SharePoint 2013。|  
  
 **概要:** 2つの Secure Store ターゲットアプリケーションを作成します。 1 つ目のターゲット アプリケーション (PowerPivotDataRefresh) を、Windows 資格情報を使用するように構成します。 2 つ目のターゲット アプリケーションを、Windows 認証をサポートしていないデータ ソース (Oracle データベースなど) の資格情報を使用して構成します。 さらに、2 つ目のターゲット アプリケーションでは、自動データ更新アカウントに 1 つ目のターゲット アプリケーションを使用します。  
  
 ![as_powerpivot_refresh_no_windows_auth](../media/as-powerpivot-refresh-no-windows-auth.gif "as_powerpivot_refresh_no_windows_auth")  
  
-   **(1) PowerPivotDatarefresh:** windows 認証で設定される Secure Store ターゲットアプリケーション ID。  
  
-   **(2) OracleAuthentication:** Oracle 資格情報で設定された Secure Store ターゲットアプリケーション ID。  
  
-   **(3)** PowerPivot サービスアプリケーションは、**自動データ更新アカウント**にターゲットアプリケーション "PowerPivotDataRefresh" を使用するように構成されています。  
  
-   **(4)** powerepivot ブックでは、Oracle データを使用します。 ブックの更新設定では、データ ソースへの接続で、資格情報にターゲット アプリケーション **(2)** を使用するよう指定します。  
  
## <a name="prerequisites"></a>前提条件  
  
-   PowerPivot サービス アプリケーションがある。  
  
-   Secure Store Service アプリケーションがある。  
  
-   PowerPivot データ モデルを含む Excel ブックがある。  
  
## <a name="to-create-a-target-application-id-that-uses-windows-authentication"></a>Windows 認証を使用するターゲット アプリケーション ID を作成するには  
  
1.  SharePoint サーバーの全体管理で **[サービス アプリケーションの管理]** をクリックします。  
  
2.  Secure Store Service アプリケーションの名前をクリックします。  
  
3.  
  **[管理]** ページで **[新規作成]** をクリックします。 ![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application")  
  
4.  
  **[Secure Store のターゲット アプリケーションを新規に作成します]** ページで、次の値を構成します。  
  
    -   **ターゲットアプリケーション ID:** PowerPivotDataRefresh.  
  
    -   **表示名:** PowerPivotDataRefresh.  
  
    -   **連絡先の電子メール:** ?  
  
    -   **ターゲットアプリケーションの種類:** グループ.  
  
    -   **ターゲットアプリケーションページの URL:** 存在.  
  
5.  **[次へ]** をクリックします。  
  
6.  [資格情報] ページで、 **[Windows ユーザー名]** と **[Windows パスワード]** の 2 つのフィールド名とフィールドの種類は既定値のままにします。  
  
7.  **[次へ]** をクリックします。  
  
8.  
  **[メンバーシップの設定]** ページで、 **[ターゲット アプリケーションの管理者]** に 1 人以上を追加し、ターゲット アプリケーションへのアクセスが必要なメンバーを追加します。  
  
9. **[OK]** をクリックします。  
  
10. 新しいターゲット アプリケーション ID が一覧に追加されます。 ターゲットアプリケーション ID を選択し、[**資格情報の設定**![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key")] をクリックします。  
  
11. Windows ユーザー名と Windows パスワードを入力して、 **[OK]** をクリックします。  
  
## <a name="to-create-a-target-application-id-that-uses-oracle-credentials"></a>Oracle 資格情報を使用するターゲット アプリケーション ID を作成するには  
  
1.  SharePoint サーバーの全体管理で **[サービス アプリケーションの管理]** をクリックします。  
  
2.  Secure Store Service アプリケーションの名前をクリックします。  
  
3.  [**管理**] ページで、[**新しい**![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application")] をクリックします。  
  
4.  
  **[Secure Store のターゲット アプリケーションを新規に作成します]** ページで、次の値を構成します。  
  
    -   **ターゲットアプリケーション ID:** OracleAuthentication.  
  
    -   **表示名:** OracleAuthentication.  
  
    -   **連絡先の電子メール:** ?  
  
    -   **ターゲットアプリケーションの種類:** グループ.  
  
    -   **ターゲットアプリケーションページの URL:** 存在.  
  
5.  **[次へ]** をクリックします。  
  
6.  [**資格情報**] ページで、最初のフィールド名`Oracle User ID`をに変更し、フィールド`User Name`の**種類**をに変更します。  
  
     2番目のフィールド名`Oracle Password`をに変更し、 `Password`フィールドの**種類**をに変更します。  
  
7.  **[次へ]** をクリックします。  
  
8.  
  **[メンバーシップの設定]** ページで、 **[ターゲット アプリケーションの管理者]** に 1 人以上を追加し、ターゲット アプリケーションへのアクセスが必要なメンバーを追加します。  
  
9. **[OK]** をクリックします。  
  
10. 新しいターゲット アプリケーション ID が一覧に追加されます。 ターゲットアプリケーション ID を選択し、[**資格情報の設定**![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key")] をクリックします。  
  
11. Oracle ユーザー ID と Oracle パスワードを入力して、 **[OK]** をクリックします。  
  
 詳細については、「 [SQL Server 認証での Secure Store の使用 (SharePoint Server 2013)](https://technet.microsoft.com/library/gg298949.aspx) 」の「SQL Server 認証用のターゲットアプリケーションhttps://technet.microsoft.com/library/gg298949.aspx)を作成するには」を参照してください。  
  
## <a name="to-configure-the-powerpivot-service-application"></a>PowerPivot サービス アプリケーションを構成するには  
  
1.  SharePoint サーバーの全体管理で [サービス アプリケーションの管理] をクリックします。  
  
2.  PowerPivot サービスアプリケーションの名前 ("既定の PowerPivot サービスアプリケーション" など) をクリックします。  
  
3.  [アクション] で **[サービス アプリケーションの設定の構成]** をクリックします。  
  
4.  [**データ更新**] セクションで、 **PowerPivot 自動データ更新アカウント**をに`PowerPivotDataRefresh`設定し、[ **OK**] をクリックします。  
  
     ![as_powerpivot_refresh_new_refresh_acount](../media/as-powerpivot-refresh-new-refresh-acount.gif "as_powerpivot_refresh_new_refresh_acount")  
  
## <a name="to-configure-the-workbook"></a>ブックを構成するには  
  
1.  PowerPivot ギャラリーでブックを参照し、[**データ更新の管理**]![as_powerpivot_refresh_manage_reresh](../media/as-powerpivot-refresh-manage-reresh.gif "as_powerpivot_refresh_manage_reresh")をクリックします。  
  
2.  
  **[データ更新の履歴]** ページが表示されたら、 **[スケジュールの構成]** をクリックします。  
  
3.  [有効****] をクリックします。  
  
4.  
  **[さらに、できるだけ早く更新を行います]** をクリックします。  
  
5.  
  **[資格情報]** で、 **[管理者によって構成されたデータ更新アカウントを使用します]** をクリックします。  
  
6.  
  **[すべてのデータ ソース]** をクリアします。  
  
7.  Oracle データを使用するデータ ソースに対して **[最新の情報に更新]** を選択します。 データ ソース名は、Microsoft Excel で、 **[データ]** タブの **[接続]** で **[プロパティ]** をクリックすると変更できます。  
  
8.  お使いのデータベース ソースで **[既定のスケジュールを使用する]** を選択します。  
  
9. 
  **[Secure Store Service (SSS) に保存された資格情報を使用してデータ ソースにログオンします。資格情報を参照するための ID を SSS ID ボックスに入力してください]** を選択します。  
  
10. [ **ID:** ] ボックスに、 `OracleAuthentication`「」と入力します。  
  
11. **[OK]** をクリックします。  
  
     " `The provided Secure Store target application is either incorrectly configured or does not exist`" のようなエラー メッセージが表示される場合があります。  
  
     一般的な解決方法として、次の 2 つが挙げられます。  
  
    -   ターゲット アプリケーション ID が正しいことを確認する。  
  
    -   ターゲット アプリケーションの資格情報を設定したことを確認する。  
  
## <a name="to-verify-data-refresh-with-the-new-authentication"></a>新しい認証を使用したデータ更新を確認するには  
 
  **[OK]** をクリックすると、 **[更新の履歴]** ページが表示されます。 前の手順で **[さらに、できるだけ早く更新を行います]** を選択したため、数分以内に、新しい項目が更新の履歴に表示されます。 タイマー ジョブ "**PowerPivot データ更新タイマー ジョブ**" の既定値は 1 分です。 履歴の更新に新しい項目が表示されない場合は、しばらく待ってから、ブラウザーを更新してください。 それでも新しい項目が表示されない場合は、タイマー ジョブの現在の値を確認してください。  
  
## <a name="more-information"></a>詳細情報  
  
-   [SharePoint 2013 で Secure Store Service を構成](https://technet.microsoft.com/library/ee806866.aspx)します。  
  
-   「 [SharePoint 2013 での PowerPivot データ更新」と「SQL Server 2012 SP1」 (Analysis Services)](https://msdn.microsoft.com/library/jj879294.aspx#bkmk_windows_auth_interactive_data_refresh)の「定期データ更新」セクションを参照してください。  
  
  
