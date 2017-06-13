---
title: "モバイル レポートにパラメーターを追加 |Reporting Services |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 113cb057-deec-40eb-abc8-f35d3900eaa6
caps.latest.revision: 12
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6fad62a6549f4b9752bde07e39f53175768a68cb
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="add-parameters-to-a-mobile-report--reporting-services"></a>モバイル レポートにパラメーターを追加する | Reporting Services
パラメーターを備えた [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] モバイル レポートを作成し、レポートをフィルター処理できるようにすることができます。 パラメーターのあるレポートは、 [ソース レポートからのドリルスルー](../../reporting-services/mobile-reports/add-drillthrough-from-a-mobile-report-to-other-mobile-reports-or-urls.md)の対象にすることもできます。 

パラメーターのあるモバイル レポートを作成するときは、少なくとも 1 つのパラメーターを持つ共有データセットを基にします。 [共有データセットでのパラメーターの作成方法](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)を参照してください。  

モバイル レポートにパラメーターを追加したら、 [クエリ文字列パラメーターを使用してレポートを開く](../../reporting-services/mobile-reports/open-a-mobile-report-with-specific-query-string-parameters-reporting-services.md)URL を作成します。

1. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion.md)] Web ポータルの上部のバーで、 **[新規]** > **[モバイル レポート]**の順に選択します。  
  
   ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png)  
     
2. **左上隅にある** [データ] [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-long.md)]タブを選択します。   
  
3. 右上隅の **[データの追加]**を選択します。  
  
4. **[レポート サーバー]**を選択し、サーバーを選びます。  
  
5. サーバー上の共有データセットに移動し、パラメーターを持つデータセットを選択します。  
  
   グリッドにデータセット内のデータが表示されます。 波かっこ **{ }** が表示された緑色の円は、データセットにパラメーターでマークを付けます。  
     
   ![SSMRP_PforParam](../../reporting-services/mobile-reports/media/ssmrp-pforparam.png)  
  
6. タブの歯車を選択し、 **[パラメーター]**({}) を選択します。  
  
   ![SSMRP_ParamWheel](../../reporting-services/mobile-reports/media/ssmrp-paramwheel.png)  
  
7. パラメーターに値を渡すレポート要素を選択します。  
  
   ![SSMRP_SetParam](../../reporting-services/mobile-reports/media/ssmrp-setparam.png)  
     
8. **[プレビュー]** を選択して、レポートがどのように表示されるかを確認します。 このレポートの選択リストでは Category パラメーターを使用しています。

   ![sql-server-mobile-report-publisher-Selection-List-View-No-Selection](../../reporting-services/mobile-reports/media/sql-server-mobile-report-publisher-selection-list-view-no-selection.png) 
   
9. 選択リストの値を選択すると、レポートはフィルターされ、その値 (この例では Accessories) が表示されます。

   ![sql-server-mobile-report-publisher-Selection-List-Category-Selected](../../reporting-services/mobile-reports/media/sql-server-mobile-report-publisher-selection-list-category-selected.png)   
  
### <a name="see-also"></a>参照  
-  [特定のクエリ文字列パラメーターを使用してモバイル レポートを開く](../../reporting-services/mobile-reports/open-a-mobile-report-with-specific-query-string-parameters-reporting-services.md)
-  [モバイル レポートから他のモバイル レポートまたは URL にドリルスルーを追加する](../../reporting-services/mobile-reports/add-drillthrough-from-a-mobile-report-to-other-mobile-reports-or-urls.md)
-  [共有データセットまたは埋め込みデータセットの作成](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)
- [Create and publish mobile reports with SQL Server Mobile Report Publisher (SQL Server Mobile Report Publisher でモバイル レポートを作成し発行する)](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
  
  


