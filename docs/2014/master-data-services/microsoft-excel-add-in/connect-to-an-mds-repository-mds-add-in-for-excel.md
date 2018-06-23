---
title: MDS リポジトリへの接続 (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f427312-4c09-4c8b-b9f9-8b235557a74b
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 5c2fd145d78c4c24d9f43a5919d53af3c3aab3c6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178457"
---
# <a name="connect-to-an-mds-repository-mds-add-in-for-excel"></a>MDS リポジトリへの接続 (Excel 用 MDS アドイン)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]では、データの読み込みまたはパブリッシュの前に MDS リポジトリに接続する必要があります。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[エクスプローラー]** 機能領域にアクセスする権限が必要です。  
  
### <a name="to-connect-to-an-mds-repository"></a>MDS リポジトリに接続するには  
  
1.  MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]の **[マスター データ]** タブの **[接続と読み込み]** グループで、 **[接続]** ボタンの下の矢印をクリックし、 **[接続の管理]** をクリックします。  
  
2.  **[接続の管理]** ダイアログ ボックスの **[新しい接続]** セクションで、 **[新しい接続の作成]** をクリックします。  
  
3.  **[新規]** をクリックします。  
  
4.  **[新しい接続の追加]** ダイアログ ボックスの **[説明]** フィールドに、接続の説明を入力します。 この接続は、ツール バーの **[接続]** ボタンの下の矢印をクリックしたときに表示されます。  
  
5.  **[MDS サーバー アドレス]** ボックスに、[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションの URL (http://contoso/mds など) を入力します。  
  
    > [!NOTE]  
    >  必ずコンピューター名を使用してください。"localhost" を使用しないでください。  
  
6.  **[OK]** をクリックします。 **[既存の接続]** セクションに名前が表示されます。  
  
7.  必要であれば、 **[テスト]** をクリックして接続をテストします。 確認ダイアログまたはエラー ダイアログが表示されます。 **[OK]** をクリックして閉じます。  
  
8.  **[接続]** をクリックします。 **[マスター データ サービス]** ペインが表示されます。  
  
## <a name="next-steps"></a>次の手順  
  
-   [MDS から Excel へのデータの読み込み](export-data-to-excel-from-master-data-services.md)  
  
-   [読み込み前にデータをフィルター処理&#40;MDS アドインを Excel 用&#41;](filter-data-before-exporting-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>参照  
 [接続 &#40;Excel 用 MDS アドイン&#41;](connections-mds-add-in-for-excel.md)  
  
  