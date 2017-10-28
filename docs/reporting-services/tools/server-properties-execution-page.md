---
title: "サーバーのプロパティ ([実行] ページ) |Microsoft ドキュメント"
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
f1_keywords:
- sql13.swb.reportserver.serverproperties.execution.f1
ms.assetid: 53b77db1-b013-4dac-82dd-30c0de276639
caps.latest.revision: 32
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 933f3287d8e02df8aeadf93bbd7ce39f20aff268
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="server-properties-execution-page"></a>[サーバーのプロパティ] [実行] ページ)
  このページを使用すると、レポート実行のタイムアウト値を設定できます。 この値は、現在のレポート サーバー インスタンスによって処理されるすべてのレポートに適用されます。 この設定は、レポートごとに上書きすることができます。 レポート サーバーで行われるすべてのレポート処理の時間に加え、レポート内で使用されるデータをレポート サーバーが取得するときにデータベース サーバーで実行されるクエリ処理に対応する時間も指定する必要があります。  
  
 このページを開くには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を起動してレポート サーバー インスタンスに接続し、レポート サーバー名を右クリックして **[プロパティ]**をクリックします。 **[実行]** をクリックするとこのページが開きます。  
  
## <a name="options"></a>オプション  
 **[レポートの実行をタイムアウトしない]**  
 レポート サーバーでレポート処理が完了するまでの時間を制限しないようにします。  
  
 **[レポートの実行を次の秒数に制限する]**  
 レポート実行の時間制限を設定します。 時間はレポートが要求されたときから測定されます。 レポートが完全に処理される前に制限時間に到達した場合、レポート サーバーは、処理および外部データ ソースに対するインプロセス クエリをすべて取り消します。  
  
## <a name="see-also"></a>参照  
 [レポート サーバーのプロパティの設定 & #40 です。Management Studio &#41;](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
 [Management Studio でのレポート サーバーに接続します。](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [レポート処理プロパティを設定します。](../../reporting-services/report-server/set-report-processing-properties.md)   
 [レポートおよび共有データセットの処理 &#40; のタイムアウト値の設定SSRS &#41;](../../reporting-services/report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)   
 [レポート サーバーの Management Studio の F1 ヘルプ](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)  
  
  

