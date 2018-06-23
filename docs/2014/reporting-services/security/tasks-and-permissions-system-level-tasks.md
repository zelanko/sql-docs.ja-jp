---
title: システムレベルのタスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- system-level tasks [Reporting Services]
ms.assetid: 7023b388-40b2-4590-b227-115cf380a1e7
caps.latest.revision: 35
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: de33e7370e141e07ac61b6e62d6d1d0cc44ffdc4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165982"
---
# <a name="system-level-tasks"></a>システムレベルのタスク
  システムレベルのタスクとは、レポート サーバー サイト全体に適用される操作に関連した権限を集めたタスクです。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] にはこの他に、特定のアイテムに適用されるアイテムレベルのタスクがあります。 詳細については、「 [アイテムレベルのタスク](tasks-and-permissions-item-level-tasks.md)」を参照してください。 タスクと一般的な権限の詳細については、次を参照してください。[タスクと権限](tasks-and-permissions.md)です。  
  
> [!NOTE]  
>  プログラムでこれらのタスクを使用して処理を実行している場合、システムレベルのタスクをサポートしているメソッドを使用する必要があります。 詳細については、「 <xref:ReportService2010.ReportingService2010.ListTasks%2A> および <xref:ReportService2010.ReportingService2010.ListRoles%2A>」を参照してください。  
  
## <a name="permissions-in-system-level-tasks"></a>システムレベルのタスクの権限  
 次の表に、一連の権限をシステム タスクごとに示します。 権限の一覧は、タスクごとに利用できる機能をより詳細に示すためにのみ記載されています。  
  
|タスク|アクセス許可|  
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
 [ネイティブ モードのレポート サーバーに対する権限の許可](granting-permissions-on-a-native-mode-report-server.md)  
  
  