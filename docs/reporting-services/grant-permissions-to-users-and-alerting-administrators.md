---
title: "ユーザーおよび警告管理者に権限を付与 |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 166808e1-ada7-48d2-bda8-8f7c017fb3aa
caps.latest.revision: 11
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 91700c92ed7f96e00ba05d7ee9ca96590d0a4837
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="grant-permissions-to-users-and-alerting-administrators"></a>ユーザーおよび警告管理者に権限を付与する

[!INCLUDE[ssrs-appliesto-sql2016-xpreview](../includes/ssrs-appliesto-sql2016-xpreview.md)][!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

ユーザーおよび警告管理者がデータ警告を作成、編集、削除、および表示できるようにするには、SharePoint 権限を付与する必要があります。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のデータ警告機能と共に使用する特別な権限はありません。組み込みの SharePoint 権限を使用します。

> [!NOTE]
> SQL Server 2016 より後に、SharePoint と reporting Services の統合を使用できなくします。

**インフォメーション ワーカー**: SharePoint の "通知の作成" 権限と "アイテムの表示" 権限が必要です。 組み込みの SharePoint 権限レベル (デザイン、投稿、読み取り、および表示のみ) には、SharePoint の "通知の作成" 権限と "アイテムの表示" 権限が含まれます。 データ警告を作成、編集、実行、および表示するユーザーをサポートするために必要な権限を持つカスタム権限レベルを作成することもできます。

**警告管理者**: SharePoint の "通知の管理" 権限が必要です。 既定では、"チーム サイト" サイト テンプレートを使用して作成されたサイトに対するこの権限は、フル コントロール権限レベルにのみ含まれます。 他のサイト テンプレートを使用した場合は、既定の SharePoint グループの、異なる一覧が表示されます。 "通知の管理" 権限を組み込みの権限レベルのいずれかに追加したり、データ警告を表示および削除する警告管理者をサポートするために必要な権限を持つカスタム権限レベルを作成したりできます。

SharePoint 権限の詳細については、「 [ユーザー権限とアクセス許可レベル (SharePoint Server 2010)](http://technet.microsoft.com/library/cc721640.aspx)」を参照してください。

## <a name="grant-permissions"></a>[アクセス許可の付与]
  
1.  権限を付与する SharePoint サイトに移動します。  
  
2.  ツール バーの **[サイトの操作]** をクリックし、 **[サイトの権限]**をクリックします。  
  
     このオプションが表示されない場合は、他のユーザーに権限を付与する権限がありません。  
  
3.  **[アクセス許可の付与]**をクリックします。  
  
4.  **[ユーザー/グループ]**ボックスに、権限を付与するユーザー名、グループ名、または電子メール アドレスを入力します。  
  
5.  **[SharePoint グループへのユーザーの追加]** または **[ユーザーにアクセス許可を直接付与する]** をクリックします。 **[SharePoint グループへのユーザーの追加]** と **[ユーザーにアクセス許可を直接付与する]** のどちらを選択したかに応じて、次のいずれかを実行します。  
  
    -   **[SharePoint グループへのユーザーの追加]**をクリックした場合は、ドロップダウン リストで権限レベルを選択します。  
  
    -   **[ユーザーにアクセス許可を直接付与する]**をクリックした場合は、権限レベルを選択します。  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  

## <a name="see-also"></a>参照

[SharePoint サイト &#40; レポート サーバー アイテムに対する権限を設定します。Reporting Services の SharePoint モード &#41; と統合](../reporting-services/security/set-permissions-for-report-server-items-on-a-sharepoint-site.md)   
[Reporting Services のデータ警告](../reporting-services/reporting-services-data-alerts.md)  

他に質問しますか。 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)
