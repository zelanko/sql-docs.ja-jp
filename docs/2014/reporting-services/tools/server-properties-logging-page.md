---
title: '[サーバーのプロパティ] ([ログ記録] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.reportserver.serverproperties.logging.f1
ms.assetid: b338deab-4868-4951-9f22-0605add2fc95
caps.latest.revision: 15
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: e92101a4a1b96ef93fde7bd19ad075d1cf27f786
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076559"
---
# <a name="server-properties-logging-page"></a>[サーバーのプロパティ]\([ログ記録] ページ)
  このページを使用すると、レポート サーバーで収集されるレポート実行データに制限を設定できます。 実行データはレポート サーバー データベースに内部的に格納されます。 ネイティブ モードまたは SharePoint 統合モードで実行されているレポート サーバーのレポート処理を追跡できます。 レポート サーバーがスケールアウト配置の一部である場合、レポート実行ログでは、配置全体に対するすべてのレポート処理のレコードが 1 つのログ ファイルで保持されます。  
  
 このページを開くを起動[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]レポート サーバーに接続をレポート サーバーの名前を右クリックし、選択**プロパティ**です。 **[ログ記録]** をクリックするとこのページが開きます。  
  
## <a name="options"></a>および  
 **[レポート実行のログ記録を有効にする]**  
 サーバーのレポート処理に関する情報を作成して保存する場合にクリックします。 このオプションを有効にした場合、レポート サーバーにより、使用されたレポートの種類、レポート処理の頻度、実行されたレポート操作の種類、出力形式、およびレポートの実行者が追跡されます。 詳細については、ログでキャプチャされる追加のデータ ポイントは、次を参照してください。[レポート サーバー実行ログと ExecutionLog3 ビュー](../report-server/report-server-executionlog-and-the-executionlog3-view.md)です。  
  
 **[次の日数が経過したログ エントリを削除する]**  
 レポート実行ログからログ エントリが削除されるまでの経過日数を指定します。 既定値は 60 日です。  
  
## <a name="see-also"></a>参照  
 [レポート サーバーのプロパティを設定する (Management Studio)](set-report-server-properties-management-studio.md)   
 [Management Studio でレポート サーバーに接続する](connect-to-a-report-server-in-management-studio.md)   
 [Reporting Services のログ ファイルとソース](../report-server/reporting-services-log-files-and-sources.md)   
 [Management Studio のレポート サーバーの F1 ヘルプ](report-server-in-management-studio-f1-help.md)   
 [レポート サーバー実行ログと ExecutionLog3 ビュー](../report-server/report-server-executionlog-and-the-executionlog3-view.md)  
  
  