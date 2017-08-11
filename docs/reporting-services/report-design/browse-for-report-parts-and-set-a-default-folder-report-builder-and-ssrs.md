---
title: "レポート パーツの参照し、既定のフォルダー (レポート ビルダーおよび SSRS) を設定 |Microsoft ドキュメント"
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
ms.assetid: 5cf38068-65d1-4fe8-81f3-a404d8fbc663
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 645e20dbc98f831a778df0397b42eea096b71dfd
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs"></a>レポート パーツの参照と既定のフォルダーの設定 (レポート ビルダーおよび SSRS)
[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の改ページ調整されたレポートを作成する最も簡単な方法は、テーブルやグラフなどの既存のレポート アイテムをレポート パーツ ギャラリーからレポートに追加することです。 レポートにレポート パーツを追加すると、動作に必要なアイテムもすべて追加されます。 たとえば、データを表示するレポート パーツは、クエリやデータ ソースへの接続などのデータセットに依存しています。 レポートにレポート パーツを追加した後、必要に応じてそのレポート パーツを変更できます。  
  
 レポート サーバーや、レポート サーバーに統合されている SharePoint サイトにレポート パーツをパブリッシュするための既定のフォルダーを設定できます。  
  
 詳細については、「[レポート パーツ (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/report-parts-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="to-browse-for-report-parts"></a>レポート パーツを参照するには  
  
1.  **[挿入]** メニューの **[レポート パーツ]**をクリックします。  
  
     まだ接続していない場合は、 **[レポート サーバーへの接続]**をクリックし、名前を入力します。  
  
    > [!NOTE]  
    >  レポート パーツを参照するには、レポート サーバーに接続している必要があります。  
  
2.  レポート パーツの詳細を指定して、検索を絞り込むことができます。 名前と説明のすべてまたは一部を **[検索]** ボックスに入力し、 **[抽出条件の追加]** をクリックして次のフィールドのいずれかまたはすべての値を追加します。  
  
    -   作成者  
  
    -   作成日  
  
    -   最終更新日  
  
    -   最終更新元  
  
    -   サーバー フォルダー  
  
    -   型  
  
     たとえば、画像を検索するには、 **[条件の追加]**、 **[種類]**の順にクリックします。 ドロップダウン ボックスの **[画像]** チェック ボックスをオンにし、Enter キーを押してから、検索の虫眼鏡アイコンをクリックします。  
  
    > [!NOTE]  
    >  **[作成者]** と **[最終更新元]** の値については、レポート サーバーを使用しているユーザー名を検索してください。  
  
## <a name="to-set-a-default-folder-for-report-parts"></a>レポート パーツの既定のフォルダーを設定するには  
  
1.  **[レポート ビルダー]**をクリックし、 **[オプション]**をクリックします。  
  
2.  **[オプション]** ダイアログ ボックスの **[設定]** タブで、 **[レポート パーツをパブリッシュする既定のフォルダー]** ボックスにフォルダー名を入力します。  
  
 レポート サーバー上にフォルダーを作成する権限があり、このフォルダーが存在していない場合は、レポート ビルダーによってフォルダーが作成されます。  
  
 この設定を有効にするためにレポート ビルダーを再起動する必要はありません。  
  
## <a name="see-also"></a>参照  
 [更新を確認するまたは更新をオフにする (レポート ビルダーおよび SSRS)](http://msdn.microsoft.com/en-us/9c69792d-d7c4-453b-ae2f-6d2d071d8606)   
 [レポート パーツと &#40;です。レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/report-parts-report-builder-and-ssrs.md)   
 [レポート パーツとレポート ビルダーでデータセット](../../reporting-services/report-data/report-parts-and-datasets-in-report-builder.md)   
 [レポート パーツのトラブルシューティング (レポート ビルダーおよび SSRS)](http://msdn.microsoft.com/en-us/d9fe1932-46e7-421b-a8a9-4c54d9576e94)   
 [およびレポート パーツ &#40; を再パブリッシュレポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/publish-and-republish-report-parts-report-builder-and-ssrs.md)  
  
  
