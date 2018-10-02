---
title: ロールを作成、削除、または変更する (Management Studio) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- roles [Reporting Services], creating
- deleting roles
- removing roles
- roles [Reporting Services], definitions
- modifying roles
- roles [Reporting Services], deleting
- roles [Reporting Services], modifying
ms.assetid: 3d1d56e6-a283-44a7-8417-36cb4d2c74d1
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 3727a1d7df04d4d46ca7058e1fd254c76f78afda
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47795060"
---
# <a name="role-definitions---create-delete-or-modify"></a>ロールの定義 - 作成、削除、または変更
  Reporting Services には、レポート サーバーへのアクセス レベルをあらかじめ定義したロールが用意されています。 レポート サーバーにアクセスする各ユーザーまたはグループは、実行できるタスクが定義されたロールを介して、レポート サーバーにアクセスすることになります。 ロールは、レポート サーバー全体に対して定義されます。 レポート サーバーの特定の部分についてロール定義を変更したり、状況に依存するようなロールを指定したりすることはできません。  
  
 ロールを作成、変更、または削除するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用します。 削除できるのは、使用されていないロールだけです。  
  
 作成したロールにユーザーおよびグループを割り当てるには、レポート マネージャーを使用します。 詳細については、「 [レポート サーバーへのユーザー アクセスを許可する &#40;レポート マネージャー&#41;](../../reporting-services/security/grant-user-access-to-a-report-server-report-manager.md)」を参照してください。  
  
> [!NOTE]  
>  レポート サーバーが SharePoint 統合モード用に構成されている場合、統合先の SharePoint サイトに接続すると、レポート サーバーのコンテンツや操作へのアクセスを制御する権限レベルを閲覧および変更できます。  
  
### <a name="to-create-a-role-definition"></a>ロールの定義を作成するには  
  
1.  オブジェクト エクスプローラーで、レポート サーバーのノードを展開します。  
  
2.  [セキュリティ] フォルダーを展開します。  
  
3.  アイテムレベルのロールの定義を作成する場合は、 **[ロール]** を右クリックし、 **[新しいロール]** をポイントします。  
  
     また、システム レベルのロールの定義を作成する場合は、 **[システム ロール]** を右クリックし、 **[新しいシステム ロール]** をポイントします。  
  
4.  ロールに対する一意の名前を入力します。 名前には、少なくとも 1 つの文字が含まれている必要があります。 スペースおよび記号を含めることもできますが、; ? : \@ & = + , $ / * < > | " or /.  
  
5.  必要に応じて、説明を入力します。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] では、この説明はこのページでのみ表示されます。 レポート マネージャーを使用してこのアイテムを表示するユーザーは、この説明をレポート マネージャーで参照できます。  
  
6.  このロールのメンバーが実行できるタスクを選択します。  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-or-modify-a-role-definition"></a>ロールの定義を削除または変更するには  
  
1.  オブジェクト エクスプローラーで、レポート サーバーのノードを展開します。  
  
2.  [セキュリティ] フォルダーを展開します。  
  
3.  アイテムレベルのロールの定義を削除または変更するには、[ロール] フォルダーを展開します。 次のいずれかを実行します。  
  
    1.  ロールの定義を削除するには、アイテムを右クリックし、 **[削除]** をクリックします。 **[オブジェクトの削除]** ダイアログ ボックスが表示されます。 [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    2.  ロールの定義を変更するには、アイテムを右クリックし、 **[プロパティ]** をクリックします。 **[ユーザー ロールのプロパティ]** ダイアログ ボックスの [全般] ページが表示されます。  
  
         このロールのメンバーが実行できるタスクを選択し、 **[OK]** をクリックします。  
  
4.  システム レベルのロールの定義を削除または変更するには、 **[システム ロール]** フォルダーを展開します。 次のいずれかを実行します。  
  
    1.  システム ロールの定義を削除するには、アイテムを右クリックし、 **[削除]** をクリックします。 **[オブジェクトの削除]** ダイアログ ボックスが表示されます。 [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    2.  システム ロールの定義を変更するには、アイテムを右クリックし、 **[プロパティ]** をクリックします。 **[システム ロールのプロパティ]** ダイアログ ボックスの [全般] ページが表示されます。  
  
         このロールのメンバーが実行できるタスクを選択し、 **[OK]** をクリックして変更を適用します。  
  
## <a name="see-also"></a>参照  
 [Management Studio でレポート サーバーに接続する](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [ロールの割り当てを作成および管理する](../../reporting-services/security/create-and-manage-role-assignments.md)   
 [SQL Server Management Studio の Reporting Services &#40;SSRS&#41;](../../reporting-services/tools/reporting-services-in-sql-server-management-studio-ssrs.md)  
  
  
