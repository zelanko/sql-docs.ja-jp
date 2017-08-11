---
title: "レポート パラメーター (レポート ビルダーおよび SSRS) の順序を変更する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: abd61e19-dba3-423c-a26c-e8bc43197d3f
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3377e943ddf7d8c7bd06aeab52ee263a754af25c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="change-the-order-of-a-report-parameter-report-builder-and-ssrs"></a>レポート パラメーターの順序の変更 (レポート ビルダーおよび SSRS)
  従属パラメーターが、そのパラメーターが依存するパラメーターの前にリストされている場合、レポート パラメーターの順序を変更します。 カスケード型パラメーターがある場合や、パラメーターの既定値をユーザーに対して示してから他のパラメーターの値をユーザーが選択する場合に、パラメーターの順序は重要です。 従属レポート パラメーターには、既定値のクエリまたは有効値のクエリのいずれかの、クエリ パラメーターへの参照が含まれます。これは、 **レポート データ** ペインのパラメーター リストでその後にあるレポート パラメーターを参照します。  
  
 レポートの実行時、レポート ビューアー ツール バーでのパラメーターの表示順は、 **レポート データ** ペインのパラメーターの順序とカスタム パラメーター ペイン内のパラメーターの場所によって決まります。 詳細については、次を参照してください[レポート &#40; のパラメーター ペインをカスタマイズする。レポート ビルダー"&"#41;](../../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-change-the-order-of-report-parameters"></a>レポート パラメーターの表示順を変更するには  
  
レポート パラメーターの表示順は、次のいずれかの操作で変更できます。  
  
-   次の図のように、 **レポート データ** ペインでパラメーターをクリックし、上矢印および下矢印ボタンを使用して、一覧内でのパラメーターの位置を移動します。  **レポート データ** ペインでパラメーターの順序を変更すると、パラメーター ペインのパラメーターの位置が変わります。  
  
     ![レポート データ ペインでパラメーターの順序を変更](../../reporting-services/report-design/media/ssrs-changeorderofparameters-reportdata.png "レポート データ ペイン内のパラメーターの順序を変更します。")  
  
-   パラメーター ペインで、パラメーターをペイン内の新しい列または行にドラッグします。 ペイン内でパラメーターの位置を変更すると、 **レポート データ** ペインのパラメーターの順序が変わります。 ペインでパラメーターを移動する方法の詳細については、次を参照してください[レポート &#40; のパラメーター ペインをカスタマイズします。。レポート ビルダー"&"#41;](../../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md).  
  
## <a name="see-also"></a>参照  
 [レポート パラメーターと &#40; です。レポート ビルダーおよびレポート デザイナーと &#41; です。](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [レポート ビルダー ダイアログ ボックス、ペイン、およびウィザードに関するヘルプ](http://msdn.microsoft.com/en-us/2da24891-0b6d-4d3c-8b18-81b98752642f)   
 [レポートと &#40; へのカスケード型パラメーターを追加します。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [チュートリアル: レポートと &#40; へのパラメーターを追加します。レポート ビルダーと &#41; です。](../../reporting-services/tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [データセット フィルター、データ領域フィルター、およびグループ フィルターと &#40; を追加します。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Parameters コレクションの参照と &#40; です。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-design/built-in-collections-parameters-collection-references-report-builder.md)  
  
  
