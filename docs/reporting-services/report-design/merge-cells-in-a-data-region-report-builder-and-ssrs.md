---
title: "(レポート ビルダーおよび SSRS) は、データ領域内のセルをマージ |Microsoft ドキュメント"
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
ms.assetid: 43551300-89b2-4f4e-af09-69084324afaf
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c643b94c86109a99e1448093b4b9744924fcd7f7
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="merge-cells-in-a-data-region-report-builder-and-ssrs"></a>データ領域内のセルの結合 (レポート ビルダーおよび SSRS)
[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のページ分割されたレポートでは、データ領域内のセルを結合すると、セルとセルの合成や、データ領域の外観の向上のほか、複数の列グループおよび行グループにまたがるラベルの指定が可能になります。  
  
コーナー、列ヘッダー、グループ定義 (または行ヘッダー)、および本文など、データ領域の各領域内でのみ、セルを結合できます。 領域の境界を越えるセルを結合することはできません。 たとえば、データ領域のコーナー領域のセルと行グループ領域のセルを結合することはできません。 詳細については、「 [テーブル、マトリックス、および一覧 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-merge-cells-in-a-data-region"></a>データ領域内のセルを結合するには  
  
1.  レポート デザイン画面上のデータ領域で、結合する最初のセルをクリックします。 マウスの左ボタンを押したまま垂直方向または水平方向にドラッグして、隣接するセルを選択します。 選択したセルは強調表示されます。  
  
2.  選択したセルを右クリックし、 **[セルの結合]**を選択します。 選択したセルが 1 つのセルに結合されます。  
  
3.  手順 1. と手順 2. を繰り返し、データ領域内で隣接する他のセルを結合します。  
  
## <a name="see-also"></a>参照  
[Tablix データ領域](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)  
 [テーブルと #40 です。レポート ビルダーおよび SSRS & #41 です。](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)   
 [マトリックスを作成します。](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md)   
 [一覧がある請求書とフォームを作成する](../../reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
[テーブル、マトリックス、および一覧 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  

