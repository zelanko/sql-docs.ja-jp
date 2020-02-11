---
title: アイテムの移動または削除 (レポート マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- moving items
- items [Reporting Services], moving
ms.assetid: 980a66c7-a18b-4af7-8954-45726fa517d6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: aafd2ff32e8c554186d18a6329649081e8babe6b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66103732"
---
# <a name="move-or-delete-an-item-report-manager"></a>アイテムの移動または削除 (レポート マネージャー)
  レポート サーバーにパブリッシュしたレポートやレポート関連アイテムは、フォルダーに格納されます。 アイテムは異なるフォルダーに移動でき、それらのアイテムへの参照はレポート サーバーによって自動的に保持されます。 アイテムを削除する前に、そのアイテムに依存しているアイテムが他に存在しないか確認してください。  
  
## <a name="move-an-item"></a>アイテムの移動  
 レポート サーバー アイテムは、レポート サーバー フォルダー階層内の異なるフォルダーに移動できます。 アイテムを移動すると、セキュリティ設定などのすべてのプロパティが、アイテムと共に新しい場所に移動します。 フォルダーを移動すると、そのフォルダーに含まれるすべてのアイテムも移動します。  
  
 レポート マネージャーでは、移動できるアイテムがフォルダー階層で示されています。 移動可能な各アイテムのアイコンを次の表に示します。  
  
|アイコン|移動可能なアイテム|  
|----------|-------------------|  
|![レポートアイコン](../media/hlp-16doc.gif "レポート アイコン")|レポート|  
|![リンク レポート アイコン](../media/hlp-16linked.gif "リンク レポート アイコン")|リンク レポート|  
|![フォルダー アイコン](../media/hlp-16folder.gif "フォルダー アイコン")|Folder|  
|![汎用リソースアイコン](../media/hlp-16file.gif "汎用リソース アイコン")|汎用リソース|  
|![共有データソースのアイコン](../media/hlp-16datasource.png "Shared data source icon")|[共有データ ソース]|  
||共有データセット|  
  
 作業に使用するすべてのアイテムを移動できるわけではありません。 サブスクリプションまたはレポート履歴など、レポートに関連付けられたアイテムを移動することはできません。 これらのアイテムは、関連するレポートと共に移動します。 同様に、フォルダー階層の外部にある、共有スケジュールなどのアイテムは移動できません。 操作を行うための権限がない場合は、アイテムを移動できません。 アイテムを移動するための権限は、当該アイテムのロールの割り当てで "レポートの管理"、"モデルの管理"、"フォルダーの管理、および "データ ソースの管理" のタスクを選択した場合に許可されます。  
  
#### <a name="to-move-an-item-from-within-the-contents-page"></a>[コンテンツ] ページでアイテムを移動するには  
  
1.  Start [レポートマネージャー &#40;SSRS ネイティブモード&#41;]../report-manager-ssrs-native-mode.md)。  
  
2.  レポート マネージャーで、 **[コンテンツ]** ページに移動し、移動するアイテムを探します。  
  
3.  アイテムの上にマウス ポインターを移動し、下矢印をクリックします。  
  
4.  ドロップダウン メニューの **[移動]** をクリックします。  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  
  **[場所]** については、アイテムの移動先のフォルダーを指定します。 フォルダーの完全修飾名を入力するか、またはツリー コントロールを使用して目的のフォルダーに移動します。  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 または、移動するオブジェクトに移動して **[プロパティ]** をクリックし、ページの上部にある **[移動]** をクリックします。  
  
## <a name="delete-an-item"></a>項目を削除する  
 アイテムを削除する前に、そのアイテムが他のアイテムによって使用されていないかどうかを確認してください。 たとえば、共有データ ソースを削除した場合、そのデータ ソースを使用するレポートおよびモデルは実行できなくなります。 レポートを削除すると、そのレポートに関連付けられているサブスクリプションおよびレポート履歴も削除されます。 アイテムの依存アイテムを検索するには、[依存アイテム] ページ &#40;レポートマネージャー&#41;] を参照してください。/dependent-items-page-report-manager.md)。  
  
#### <a name="to-delete-a-report-or-item"></a>レポートまたはアイテムを削除するには  
  
1.  Start [レポートマネージャー &#40;SSRS ネイティブモード&#41;]../report-manager-ssrs-native-mode.md)。  
  
2.  レポート マネージャーで、 **[コンテンツ]** ページに移動し、削除するアイテムを探します。  
  
3.  アイテムの上にマウス ポインターを移動し、下矢印をクリックします。  
  
4.  ドロップダウン メニューの **[削除]** をクリックします。  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [コンテンツページ &#40;レポートマネージャー&#41;]../contents-page-report-manager.md)   
 [レポートの検索、表示、管理 &#40;レポート ビルダーおよび SSRS&#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
