---
title: "レポートおよびその他のアイテム (レポート ビルダーおよび SSRS) の検索 |Microsoft ドキュメント"
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
ms.assetid: 6a586659-5c2b-453b-8f40-a3a469277b17
caps.latest.revision: 7
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: e3c41db09cbe1387545b72fd2942e4b30e71d1fd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="searching-for-reports-and-other-items-report-builder--and-ssrs"></a>レポートおよび他のアイテムの検索 (レポート ビルダーおよび SSRS)
  レポート マネージャーを使用して、名前や説明からレポート サーバーの特定のアイテムを検索できます。 検索できるアイテムは、パブリッシュされているレポート、レポート モデル、フォルダー、共有データ ソース、およびリソースです。 スケジュール、所有者、ロールの割り当て、レポート履歴の特定のスナップショット、またはサブスクリプションは検索できません。 検索は、アイテムが保存されているレポート サーバー データベースに対して実行されます。  
  
> [!NOTE]  
>  ファイル システムの検索を実行しても、レポート サーバーによって管理されているアイテムの検索結果は返されません。  
  
-   レポート マネージャーでアイテムを検索するには、ページの先頭にある **[検索]** テキスト ボックスに検索文字列を入力します。 検索は、フォルダー階層の最上位ノードから開始され、続いて各分岐にわたり実行されます。 特定の分岐へのアクセス権がない場合、その分岐は検索されません。 これには、他のユーザーが所有する [個人用レポート] フォルダー、および通常アクセスできない他のフォルダーが該当します。 検索結果には、表示権限のあるレポートやアイテムのみが表示されます。  
  
-   名前や説明からアイテムを検索するには、検索したいテキストのすべてまたは一部を指定します。 検索文字列の大文字と小文字は区別されません。 検索条件の指定や除外を行う正符号 (+) や負符号 (-) などの検索演算子は使用できません。  
  
-   レポート内の特定のテキストを検索するには、レポートの最上部にあるツール バーを使用します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a>参照  
 [検索およびレポート マネージャー &#40; でレポートを表示します。レポート ビルダーおよび SSRS &#41;](finding-and-viewing-reports-with-a-browser-report-builder-and-ssrs.md)   
 [個人用レポート &#40; を使用します。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-builder/using-my-reports-report-builder-and-ssrs.md)   
 [レポートの検索、表示、管理 (レポート ビルダーおよび SSRS)](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [開いたり、閉じたり、レポートと #40 です。レポート マネージャー &#41;](../../reporting-services/reports/open-and-close-a-report-report-manager.md)  
  
  
