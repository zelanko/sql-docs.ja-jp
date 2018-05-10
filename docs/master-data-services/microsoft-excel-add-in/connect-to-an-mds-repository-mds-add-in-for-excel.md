---
title: MDS リポジトリへの接続 (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.component: microsoft-excel-add-in
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8f427312-4c09-4c8b-b9f9-8b235557a74b
caps.latest.revision: 12
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: c2e42b0d9567fc8cae85c9134e9169011fdf520d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="connect-to-an-mds-repository-mds-add-in-for-excel"></a>MDS リポジトリへの接続 (Excel 用 MDS アドイン)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]では、データの読み込みまたはパブリッシュの前に MDS リポジトリに接続する必要があります。  
  
## <a name="prerequisites"></a>Prerequisites  
 この手順を実行するには  
  
-   **[エクスプローラー]** 機能領域にアクセスする権限が必要です。  
  
### <a name="to-connect-to-an-mds-repository"></a>MDS リポジトリに接続するには  
  
1.  MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]の **[マスター データ]** タブの **[接続と読み込み]** グループで、 **[接続]** ボタンの下の矢印をクリックし、 **[接続の管理]** をクリックします。  
  
2.  **[接続の管理]** ダイアログ ボックスの **[新しい接続]** セクションで、 **[新しい接続の作成]** をクリックします。  
  
3.  **[新規作成]** をクリックします。  
  
4.  **[新しい接続の追加]** ダイアログ ボックスの **[説明]** フィールドに、接続の説明を入力します。 この接続は、ツール バーの **[接続]** ボタンの下の矢印をクリックしたときに表示されます。  
  
5.  **[MDS サーバー アドレス]** ボックスに、[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションの URL (`http://contoso/mds` など) を入力します。  
  
    > [!NOTE]  
    >  必ずコンピューター名を使用してください。"localhost" を使用しないでください。  
  
6.  **[OK]** をクリックします。 **[既存の接続]** セクションに名前が表示されます。  
  
7.  必要であれば、 **[テスト]** をクリックして接続をテストします。 確認ダイアログまたはエラー ダイアログが表示されます。 **[OK]** をクリックして閉じます。  
  
8.  **[接続]** をクリックします。 **[マスター データ サービス]** ペインが表示されます。  
  
## <a name="next-steps"></a>Next Steps  
  
-   [マスター データ サービスから Excel へのデータのエクスポート](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)  
  
-   [エクスポート前のデータのフィルター処理 (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/filter-data-before-exporting-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>参照  
 [接続 (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/connections-mds-add-in-for-excel.md)  
  
  
