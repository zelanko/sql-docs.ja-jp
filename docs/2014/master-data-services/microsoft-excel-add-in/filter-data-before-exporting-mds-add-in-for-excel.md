---
title: 読み込み前にデータをフィルター処理する (Excel 用 MDS アドイン) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9e30eae0-776b-4a09-aac3-0c0249d92ca5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c864e95a075477b80bdbbe06912be37bba33fadf
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84961145"
---
# <a name="filter-data-before-loading-mds-add-in-for-excel"></a>読み込み前のデータのフィルター処理 (Excel 用 MDS アドイン)
  で [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 、Excel に読み込むデータのサイズまたは範囲を制限する場合は、データをフィルター処理します。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[エクスプローラー]** 機能領域にアクセスする権限が必要です。  
  
### <a name="to-filter-data-before-loading"></a>読み込み前にデータをフィルター処理するには  
  
1.  Excel を開いて、 **[マスター データ]** タブで MDS リポジトリに接続します。 詳細については、「[MDS リポジトリへの接続 (Excel 用 MDS アドイン)](connect-to-an-mds-repository-mds-add-in-for-excel.md)」を参照してください。  
  
2.  **[マスター データ エクスプローラー]** ペインで、モデルおよびバージョンを選択します。 エンティティの一覧が作成されます。  
  
    -   **[マスター データ エクスプローラー]** ペインが表示されない場合は、 **[接続と読み込み]** グループの **[エクスプローラーの表示]** をクリックします。  
  
    -   **[マスター データ エクスプローラー]** ペインが無効になっている場合は、既存のシートに MDS によって管理されるデータが既に含まれています。 ペインを有効にするには、新しいワークシートを開きます。  
  
3.  **[マスター データ エクスプローラー]** ペインのエンティティの一覧で、フィルター処理するエンティティをクリックします。  
  
4.  リボンの **[接続と読み込み]** グループで、 **[フィルター]** をクリックします。  
  
5.  **[フィルター]** ダイアログ ボックスで、表示する属性 (列) を選択して列の順序を設定し、必要に応じて、返される行が少なくなるようにデータをフィルター処理します。 **[概要]** ペインで、返されるデータ量を確認します。 詳細については、「[[フィルター] ダイアログ ボックス (Excel 用 MDS アドイン)](filter-dialog-box-mds-add-in-for-excel.md)」を参照してください。  
  
6.  **[データの読み込み]** をクリックします。 シートに MDS によって管理されるデータが入力されます。  
  
    > [!NOTE]  
    >  -   最初の 100 万個のメンバーだけが Excel に読み込まれます。  
    > -   制約リスト (ドメインベースの属性) の列では、最初の1000値のみが読み込まれます。  
  
## <a name="next-steps"></a>次の手順  
 [Excel から MDS へのデータのパブリッシュ &#40;Excel 用 MDS アドイン&#41;](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>参照  
 [データ &#40;Excel 用 MDS アドインの読み込み&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [[フィルター] ダイアログボックス &#40;Excel 用 MDS アドイン&#41;](filter-dialog-box-mds-add-in-for-excel.md)   
 [列の並べ替え (Excel 用 MDS アドイン)](reorder-columns-mds-add-in-for-excel.md)  
  
  
