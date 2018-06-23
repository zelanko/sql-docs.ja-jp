---
title: '[セキュリティ] ページ、サイトの設定 ( レポート マネージャー) |Microsoft ドキュメント'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acc9a905-90f8-4544-aec6-b2ab3a1b0015
caps.latest.revision: 26
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: b4115675e8f9529873eeeec5f71d2b5861fef9eb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176102"
---
# <a name="security-page-site-settings-report-manager"></a>[セキュリティ] ページ、サイトの設定 ( レポート マネージャー)
  [セキュリティ] ページは、レポート サーバー サイトへのアクセスを制御するシステム ロールの割り当てを表示するために使用します。 システム ロールの割り当ては、レポート サーバー名前空間やフォルダー階層の外の領域でも有効です。 システム ロールの割り当てはグローバルであり、特定のアイテムによって変わることがありません。 システム ロールの割り当てによってサポートされる操作には、共有スケジュールの作成と使用、レポート ビルダーの使用、および一部のサーバー機能の既定値の設定が含まれます。  
  
 レポート サーバーのインストール時に、既定のシステム ロールの割り当てが作成されます。 このシステム ロールの割り当てによって、ローカルのシステム管理者にレポート サーバー環境を管理する権限が与えられます。 ローカルのシステム管理者は、システム ロールの割り当てが削除された場合でも、常にローカル レポート サーバーのセキュリティを設定できます。  
  
 レポート ビルダーまたは共有スケジュールにアクセスする必要がある他のすべてのユーザーは、システム ロールの割り当てに割り当てられます。  
  
## <a name="navigation"></a>ナビゲーション  
 ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。  
  
###### <a name="to-open-the-security-page-for-site-settings"></a>[サイトの設定] の [セキュリティ] ページを開くには  
  
1.  レポート マネージャーを開きます。  
  
2.  ページの上部にある **[サイトの設定]** をクリックします。 この操作により、サイトの [全般] プロパティ ページが開きます。  
  
3.  **[セキュリティ]** タブをクリックします。  
  
## <a name="options"></a>および  
 **Delete**  
 既存のロールの割り当てを削除する場合にクリックします。 削除するグループ名またはユーザー名の横のチェック ボックスをオンにしてから、 **[削除]** をクリックします。 1 つしか残っていないロールの割り当ては削除できません。 ロールの割り当てを削除しても、グループ アカウントやユーザー アカウント、またはロールの定義は削除されません。  
  
 **新しいロールの割り当て**  
 クリックすると、[新しいシステム ロールの割り当て] ページが開きます。このページは、レポート サーバー サイトの新たなシステム ロールの割り当てを作成するために使用します。 詳細については、次を参照してください。[新しいシステム ロールの割り当て: システムの役割の割り当て ページを編集&#40;レポート マネージャー&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md)です。  
  
 **[編集]**  
 クリックすると、[システム ロールの割り当てを編集] ページが開きます。このページは、レポート サーバー サイトの個別のシステム ロールの割り当てを編集するために使用します。 詳細については、次を参照してください。[新しいシステム ロールの割り当て: システムの役割の割り当て ページを編集&#40;レポート マネージャー&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md)です。  
  
 **グループまたはユーザー**  
 既存のロールの割り当ての一部であるグループおよびユーザーが一覧表示されます。 この列には、現在のフォルダーに対する既存のロールの割り当てが定義されているグループおよびユーザーが表示されます。 ロールの割り当ての詳細を表示または編集するには、グループ名またはユーザー名の横にある **[編集]** をクリックします。  
  
 **Roles**  
 既存のロールの割り当ての一部であるロールの定義が 1 つ以上表示されます。 1 つのグループ アカウントまたは 1 つのユーザー アカウントに複数のロールが割り当てられている場合、そのグループまたはユーザーは、すべてのロールに属するすべてのタスクを実行できます。 表示するには、一連の各ロールでサポートされているタスクを使用して[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]です。 レポート マネージャーでロールを表示、作成、変更、または削除することはできません。 手順については、次を参照してください。[作成、削除、またはロールを変更&#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md)です。  
  
## <a name="see-also"></a>参照  
 [レポート マネージャーの F1 ヘルプ](../../2014/reporting-services/report-manager-f1-help.md)   
 [ネイティブ モードのレポート サーバーに対する権限の許可](security/granting-permissions-on-a-native-mode-report-server.md)  
  
  