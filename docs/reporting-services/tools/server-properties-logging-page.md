---
title: "[サーバーのプロパティ] ([ログ記録] ページ) | Microsoft Docs"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.reportserver.serverproperties.logging.f1
ms.assetid: b338deab-4868-4951-9f22-0605add2fc95
caps.latest.revision: 17
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f1050ecd33c0e56733acdfa1732b9897517e2c43
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="server-properties-logging-page"></a>[サーバーのプロパティ]\([ログ記録] ページ)
  [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] で、この [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] ページを使用すると、レポート サーバーで収集されるレポート実行データに制限を設定できます。 実行データはレポート サーバー データベースに内部的に格納されます。 ネイティブ モードまたは SharePoint 統合モードで実行されているレポート サーバーのレポート処理を追跡できます。 レポート サーバーがスケールアウト配置の一部である場合、レポート実行ログでは、配置全体に対するすべてのレポート処理のレコードが 1 つのログ ファイルで保持されます。  
  
 このページを開くには:
 1) コントロール パネルの  ◆セグ : 文が分断されているため、訳の位置が入れ替わっています◇ [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]
 2) レポート サーバーに接続します。
 3) レポート サーバー名を右クリックして、 **[プロパティ]**をクリックします。 
 4) **[ログ記録]** をクリックするとこのページが開きます。  
  
## <a name="options"></a>オプション  
 **[レポート実行のログ記録を有効にする]**  
 サーバーのレポート処理に関する情報を作成して保存する場合にクリックします。 このオプションを有効にした場合、レポート サーバーにより、使用されたレポートの種類、レポート処理の頻度、実行されたレポート操作の種類、出力形式、およびレポートの実行者が追跡されます。 ログにキャプチャされるその他のデータ ポイントの詳細については、「 [レポート サーバー ExecutionLog と ExecutionLog3 ビュー](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md)」を参照してください。  
  
 **[次の日数が経過したログ エントリを削除する]**  
 レポート実行ログからログ エントリが削除されるまでの経過日数を指定します。 既定値は 60 日です。  
  
## <a name="see-also"></a>参照  
 [レポート サーバーのプロパティの設定 & #40 です。Management Studio &#41;](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
 [Management Studio でレポート サーバーに接続する](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [Reporting Services のログ ファイルとソース](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)   
 [Management Studio のレポート サーバーの F1 ヘルプ](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [レポート サーバー ExecutionLog と ExecutionLog3 ビュー](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md)  
  
  

