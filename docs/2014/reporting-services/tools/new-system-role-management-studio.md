---
title: 新しいシステム ロール (Management Studio) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.newsystemrole.f1
ms.assetid: 7b4a0b98-975b-478a-8359-7db39ccbb347
caps.latest.revision: 27
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 4d23cf7a0b557b4bbc687514b120af7a93cbf375
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39083028"
---
# <a name="new-system-role-management-studio"></a>[新しいシステム ロール]\(Management Studio)
  このページを使用すると、システムレベルのロールの定義を作成できます。 システム ロールの定義には、レポート サーバー全体に適用する、システムレベルのタスクのセットを指定します。  
  
> [!NOTE]  
>  ロールの定義は、ネイティブ モードで実行されているレポート サーバーでのみ使用されます。 レポート サーバーが SharePoint 統合モード用に構成されている場合、このページは使用できません。  
  
## <a name="options"></a>および  
 **名前**  
 ロールの定義名を入力します。 ロールの定義名は、レポート サーバーの名前空間内で一意である必要があります。 名前には、少なくとも 1 つの英数字が含まれている必要があります。 また、スペースおよびいくつかの記号を含めることもできます。 名前を指定するときに使用できない記号は次のとおりです。  
  
 ; ? : \@ & = +, $/* \< >  
  
 " /  
  
 **[説明]**  
 ロールの使用方法を説明する場合やロールがサポートする内容を列挙する場合に説明を表示します。  
  
 **タスク**  
 このロールで実行できるシステムレベル タスクを選択します。 新しいタスクを作成したり、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]によってサポートされている既存のタスクを変更したりすることはできません。 システム ロール定義にはアイテムレベル タスクを選択できません。  
  
 **タスクの説明**  
 タスクでサポートされる操作または権限を列挙する、タスクの説明を表示します。  
  
## <a name="see-also"></a>参照  
 [Management Studio のレポート サーバーの F1 ヘルプ](report-server-in-management-studio-f1-help.md)   
 [ロールの定義](../security/role-definitions.md)  
  
  
