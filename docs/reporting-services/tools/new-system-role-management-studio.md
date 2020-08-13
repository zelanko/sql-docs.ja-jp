---
title: 新しいシステム ロール (Management Studio) |Microsoft ドキュメント
description: Management Studio の [新しいシステム ロール] ページについて説明します。そこでは、レポート サーバー全体に適用される一連のタスクを指定するシステムレベルのロールの定義を作成します。
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.newsystemrole.f1
ms.assetid: 7b4a0b98-975b-478a-8359-7db39ccbb347
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 22c3442e16503fd58f8fcb099018b88ab6bfbf92
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "86915540"
---
# <a name="new-system-role-management-studio"></a>[新しいシステム ロール]\(Management Studio)
  このページを使用すると、システムレベルのロールの定義を作成できます。 システム ロールの定義には、レポート サーバー全体に適用する、システムレベルのタスクのセットを指定します。  
  
> [!NOTE]  
>  ロールの定義は、ネイティブ モードで実行されているレポート サーバーでのみ使用されます。 レポート サーバーが SharePoint 統合モード用に構成されている場合、このページは使用できません。  
  
## <a name="options"></a>オプション  
 **名前**  
 ロールの定義名を入力します。 ロールの定義名は、レポート サーバーの名前空間内で一意である必要があります。 名前には、少なくとも 1 つの英数字が含まれている必要があります。 また、スペースおよびいくつかの記号を含めることもできます。 名前を指定するときに使用できない記号は次のとおりです。  
  
 ; ? : \@ & = + , $ / * < >  
  
 " /  
  
 **説明**  
 ロールの使用方法を説明する場合やロールがサポートする内容を列挙する場合に説明を表示します。  
  
 **タスク**  
 このロールで実行できるシステムレベル タスクを選択します。 新しいタスクを作成したり、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]によってサポートされている既存のタスクを変更したりすることはできません。 システム ロール定義にはアイテムレベル タスクを選択できません。  
  
 **タスクの説明**  
 タスクでサポートされる操作または権限を列挙する、タスクの説明を表示します。  
  
## <a name="see-also"></a>参照  
 [Management Studio のレポート サーバーの F1 ヘルプ](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [ロールの定義](../../reporting-services/security/role-definitions.md)  
  
  
