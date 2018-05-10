---
title: システム ロールのプロパティ (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: tools
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.systemroleproperties.f1
ms.assetid: 0210fc2a-74fb-41dd-8e39-4830047ec417
caps.latest.revision: 30
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: cfdabae614e68fe91921850a7aa7a7a624f87516
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="system-role-properties-management-studio"></a>システム ロールのプロパティ (Management Studio)
  [システム ロール] ページは、レポート サーバーで現在定義されているシステム ロールの定義を表示するために使用します。 システム ロールの定義には、個別のアイテムではなく、サイト全体に関連して実行される名前付きのタスクのコレクションが含まれています。 ロールの定義は、ロールの割り当てを作成するために、ユーザーまたはグループに割り当てられます。 ロールの定義のタスクには、ユーザーまたはグループが実行できる操作を指定します。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、 **システム管理者** と **システム ユーザー**という 2 つのシステム ロールがあらかじめ定義されています。 タスクの一覧を変更することにより、ロールの定義を変更できます。また、異なるタスクの組み合わせをサポートする新しいシステム ロールを作成できます。 ロールの定義を編集すると、そのロールの定義を含むすべてのロールの割り当てに反映されます。  
  
> [!NOTE]  
>  システム ロールの割り当ては、ネイティブ モードで実行されているレポート サーバーでのみ使用されます。 レポート サーバーが SharePoint 統合モード用に構成されている場合、このページは使用できません。  
  
## <a name="options"></a>および  
 **名前**  
 システム ロールの定義名を指定します。  
  
 **[説明]**  
 システム ロール定義の説明が表示されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]では、この説明は、このページにのみ表示されます。 レポート マネージャーを使用してこのアイテムを表示すると、フォルダー階層を参照しているときにこの説明が表示される場合があります。  
  
 **タスク**  
 このロール定義で選択できるシステムレベルのタスクがすべて一覧表示されます。 定義済みタスクの一覧にアイテムを追加または一覧から削除することで、ユーザーがこのロールを使用して特定のアイテムにアクセスする方法を定義できます。 新しいタスクを作成したり、既存のタスクを変更したりすることはできません。  
  
 **[説明]**  
 各タスクに関する情報が表示されます。 タスクの説明を変更することはできません。  
  
## <a name="see-also"></a>参照  
 [Management Studio のレポート サーバーの F1 ヘルプ](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [システムレベルのタスク](../../reporting-services/security/tasks-and-permissions-system-level-tasks.md)   
 [タスクと権限](../../reporting-services/security/tasks-and-permissions.md)   
 [定義済みロール](../../reporting-services/security/role-definitions-predefined-roles.md)  
  
  
