---
title: "作成、削除、またはロール (Management Studio) の変更 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- roles [Reporting Services], creating
- deleting roles
- removing roles
- roles [Reporting Services], definitions
- modifying roles
- roles [Reporting Services], deleting
- roles [Reporting Services], modifying
ms.assetid: 3d1d56e6-a283-44a7-8417-36cb4d2c74d1
caps.latest.revision: 42
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 42f66d05b179ee5f00c3322a2eb2943439936bcb
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="role-definitions---create-delete-or-modify"></a>ロールの定義の作成、削除、または変更
  Reporting Services には、レポート サーバーへのアクセス レベルをあらかじめ定義したロールが用意されています。 レポート サーバーにアクセスする各ユーザーまたはグループは、実行できるタスクが定義されたロールを介して、レポート サーバーにアクセスすることになります。 ロールは、レポート サーバー全体に対して定義されます。 レポート サーバーの特定の部分についてロール定義を変更したり、状況に依存するようなロールを指定したりすることはできません。  
  
 ロールを作成、変更、または削除するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用します。 削除できるのは、使用されていないロールだけです。  
  
 作成したロールにユーザーおよびグループを割り当てるには、レポート マネージャーを使用します。 詳細については、「[レポート サーバーへのユーザー アクセスを許可する (レポート マネージャー)](../../reporting-services/security/grant-user-access-to-a-report-server-report-manager.md)」を参照してください。  
  
> [!NOTE]  
>  レポート サーバーが SharePoint 統合モード用に構成されている場合、統合先の SharePoint サイトに接続すると、レポート サーバーのコンテンツや操作へのアクセスを制御する権限レベルを閲覧および変更できます。  
  
### <a name="to-create-a-role-definition"></a>ロールの定義を作成するには  
  
1.  オブジェクト エクスプローラーで、レポート サーバーのノードを展開します。  
  
2.  [セキュリティ] フォルダーを展開します。  
  
3.  アイテムレベルのロールの定義を作成する場合は、 **[ロール]**を右クリックし、 **[新しいロール]**をポイントします。  
  
     また、システム レベルのロールの定義を作成する場合は、 **[システム ロール]**を右クリックし、 **[新しいシステム ロール]**をポイントします。  
  
4.  ロールに対する一意の名前を入力します。 名前には、少なくとも 1 つの文字が含まれている必要があります。 スペースおよび記号を含めることもできますが、; ?  : @ & = + , $ / * < > | " または / は含めることができません。  
  
5.  必要に応じて、説明を入力します。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] では、この説明はこのページでのみ表示されます。 レポート マネージャーを使用してこのアイテムを表示するユーザーは、この説明をレポート マネージャーで参照できます。  
  
6.  このロールのメンバーが実行できるタスクを選択します。  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-or-modify-a-role-definition"></a>ロールの定義を削除または変更するには  
  
1.  オブジェクト エクスプローラーで、レポート サーバーのノードを展開します。  
  
2.  [セキュリティ] フォルダーを展開します。  
  
3.  アイテムレベルのロールの定義を削除または変更するには、[ロール] フォルダーを展開します。 次のいずれかを実行します。  
  
    1.  ロールの定義を削除するには、アイテムを右クリックし、 **[削除]**をクリックします。 **[オブジェクトの削除]** ダイアログ ボックスが表示されます。 [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    2.  ロールの定義を変更するには、アイテムを右クリックし、 **[プロパティ]**をクリックします。 **[ユーザー ロールのプロパティ]** ダイアログ ボックスの [全般] ページが表示されます。  
  
         このロールのメンバーが実行できるタスクを選択し、 **[OK]**をクリックします。  
  
4.  システム レベルのロールの定義を削除または変更するには、 **[システム ロール]** フォルダーを展開します。 次のいずれかを実行します。  
  
    1.  システム ロールの定義を削除するには、アイテムを右クリックし、 **[削除]**をクリックします。 **[オブジェクトの削除]** ダイアログ ボックスが表示されます。 [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    2.  システム ロールの定義を変更するには、アイテムを右クリックし、 **[プロパティ]**をクリックします。 **[システム ロールのプロパティ]** ダイアログ ボックスの [全般] ページが表示されます。  
  
         このロールのメンバーが実行できるタスクを選択し、 **[OK]** をクリックして変更を適用します。  
  
## <a name="see-also"></a>参照  
 [Management Studio でのレポート サーバーに接続します。](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [作成および管理ロールの割り当て](../../reporting-services/security/create-and-manage-role-assignments.md)   
 [Reporting Services の SQL Server Management Studio & #40 です。SSRS &#41;](../../reporting-services/tools/reporting-services-in-sql-server-management-studio-ssrs.md)  
  
  

