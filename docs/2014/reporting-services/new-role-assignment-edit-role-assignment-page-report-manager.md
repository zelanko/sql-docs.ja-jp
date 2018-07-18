---
title: 新しいロールの割り当ての編集の役割の割り当て ページ (レポート マネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3319ced0-4b86-42af-b18d-da41a625113c
caps.latest.revision: 30
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 0d1635c6b9c801b5a2ad9a2eff107c3bf35cf23a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37179649"
---
# <a name="new-role-assignment-edit-role-assignment-page-report-manager"></a>[新しいロールの割り当て]: [ロールの割り当てを編集] ページ (レポート マネージャー)
  レポート サーバーのアイテムと操作に対する権限を与えるには、[新しいロールの割り当て] ページまたは [ロールの割り当てを編集] ページを使用します。 レポート サーバーへのアクセスを必要とするユーザーごとに、アクセスのレベルを定義するロールの割り当てが必要です。 ロールの割り当ては、ルート ノードか、特定のレポート、モデル、フォルダー、リソース、または共有データ ソースに作成できます。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のセキュリティは、アイテムに適用するロールの割り当てによって設定されます。 ロールの割り当てにより、グループまたはユーザーをロールの定義と適合させます。各ロールの定義により、特定のアイテムに対してグループまたはユーザーが実行できるタスクが識別されます。  
  
 アイテム レベルのロールの割り当ては、広い範囲に影響を与えることがあります。 アイテム レベルのロールの割り当ては、単一のレポートまたはフォルダーと関連付けることができますが、フォルダー階層の高いレベルで定義し、ツリーの子フォルダーおよび子アイテムに継承することも可能です。 詳細については、「[レポート サーバーへのユーザー アクセスを許可する (レポート マネージャー)](security/grant-user-access-to-a-report-server.md)」を参照してください。  
  
## <a name="navigation"></a>ナビゲーション  
 ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。  
  
###### <a name="to-open-the-new-role-assignment-or-edit-role-assignment-page"></a>[新しいロールの割り当て] ページまたは [ロールの割り当てを編集] ページを開くには  
  
1.  レポート マネージャーを開き、新しいロールの割り当てを追加するアイテムか、ロールの割り当てを編集するアイテムを探します。  
  
2.  アイテムの上にマウス ポインターを移動し、下矢印をクリックします。  
  
3.  ドロップダウン メニューの **[セキュリティ]** をクリックします。 この操作により、アイテムの [セキュリティ] プロパティ ページが開きます。  
  
4.  新しいロールの割り当てを追加する場合は、ツール バーの **[新しいロールの割り当て]** をクリックします。 ロールの割り当てを編集する場合は、編集するグループまたはユーザーの名前の隣にある **[編集]** をクリックします。  
  
    > [!NOTE]  
    >  アイテムが現在、親アイテムからセキュリティを継承している場合は、ツール バーの **[アイテムのセキュリティを編集]** をクリックしてセキュリティの設定を変更します。  
  
## <a name="options"></a>および  
 **グループ名またはユーザー名**  
 ロールの割り当てが作成されるグループ アカウントまたはユーザー アカウントの名前を入力します。 グループ名またはユーザー名は、有効な Windows ドメイン アカウントである必要があります。 この形式でアカウントを入力します:\<ドメイン >\\< アカウント\>します。  
  
> [!NOTE]  
>  このボックスは、[新しいロールの割り当て] ページでのみ使用できます。  
  
 **ロール**  
 アイテムのセキュリティの定義に使用できる、レポート サーバーで定義されているすべてのロールを表示します。 レポートやフォルダーへのロールの割り当てを作成または変更する場合、1 つ以上のロールを選択して、ユーザーが実行する必要のある操作が一連のタスクとして記述されるようにします。 各ロールでサポートされているタスクのセットを表示する使用[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]します。 レポート マネージャーでロールを表示、作成、変更、または削除することはできません。 手順については、次を参照してください。[作成、削除、またはロールを変更&#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md)します。  
  
 **[説明]**  
 ロールに関する詳細を表示します。 **閲覧者** や **コンテンツ マネージャー**などの定義済みロールに関しては、各ロールでサポートされているタスクの要約が説明として提供されます。  
  
 **ロールの割り当てを削除します。**  
 ユーザーまたはグループの既存のロールの割り当てを削除する場合にクリックします。 残っているロールの割り当てが 1 つのみである場合、そのロールの割り当てを削除することはできません (各アイテムは、ロールの割り当てを少なくとも 1 つ保持している必要があります)。  
  
> [!NOTE]  
>  このボタンは、[ロールの割り当てを編集] ページでのみ使用できます。  
  
## <a name="see-also"></a>参照  
 [ロールを作成、削除、または変更する (Management Studio)](security/role-definitions-create-delete-or-modify.md)   
 [ネイティブ モードのレポート サーバーに対する権限の許可](security/granting-permissions-on-a-native-mode-report-server.md)   
 [レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [レポート マネージャー F1 ヘルプ](../../2014/reporting-services/report-manager-f1-help.md)   
 [ロールの割り当て](security/role-assignments.md)   
 [レポート サーバーへのアクセスを与えるユーザー&#40;レポート マネージャー&#41;](security/grant-user-access-to-a-report-server.md)  
  
  
