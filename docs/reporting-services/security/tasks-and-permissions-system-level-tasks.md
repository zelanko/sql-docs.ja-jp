---
title: "システム レベルのタスク |Microsoft ドキュメント"
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
- system-level tasks [Reporting Services]
ms.assetid: 7023b388-40b2-4590-b227-115cf380a1e7
caps.latest.revision: 36
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 8f8eac1d05b8bdd034879cb2eba1c4fc867fce66
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="tasks-and-permissions---system-level-tasks"></a>タスクと権限のシステム レベルのタスク
  システムレベルのタスクとは、レポート サーバー サイト全体に適用される操作に関連した権限を集めたタスクです。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] にはこの他に、特定のアイテムに適用されるアイテムレベルのタスクがあります。 詳細については、「 [アイテムレベルのタスク](../../reporting-services/security/tasks-and-permissions-item-level-tasks.md)」を参照してください。 一般的なタスクおよび権限の詳細については、「 [タスクと権限](../../reporting-services/security/tasks-and-permissions.md)」を参照してください。  
  
> [!NOTE]  
>  プログラムでこれらのタスクを使用して処理を実行している場合、システムレベルのタスクをサポートしているメソッドを使用する必要があります。 詳細については、次を参照してください。<xref:ReportService2010.ReportingService2010.ListTasks%2A>と<xref:ReportService2010.ReportingService2010.ListRoles%2A>です。  
  
## <a name="permissions-in-system-level-tasks"></a>システムレベルのタスクの権限  
 次の表に、一連の権限をシステム タスクごとに示します。 権限の一覧は、タスクごとに利用できる機能をより詳細に示すためにのみ記載されています。  
  
|タスク|Permissions|  
|----------|-----------------|  
|レポート定義の実行|レポート定義の実行 (権限とタスクの名前が同じです)|  
|イベントの生成|イベントの生成|  
|ジョブの管理|システム プロパティの読み取り<br /><br /> システム プロパティの更新|  
|レポート サーバーのプロパティを管理|システム プロパティの読み取り<br /><br /> システム プロパティの更新|  
|ロールの管理|ロールの作成<br /><br /> ロールの削除<br /><br /> ロールのプロパティの読み取り<br /><br /> ロールのプロパティの更新|  
|共有スケジュールの管理|スケジュールの作成|  
|レポート サーバーのセキュリティを管理|システムのセキュリティ ポリシーの読み取り<br /><br /> システムのセキュリティ ポリシーの更新|  
|レポート サーバーのプロパティを表示|システム プロパティの読み取り|  
|共有スケジュールの表示|スケジュールの読み取り|  
  
## <a name="see-also"></a>参照  
 [ネイティブ モードのレポート サーバーに対する権限の許可](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
  
  
