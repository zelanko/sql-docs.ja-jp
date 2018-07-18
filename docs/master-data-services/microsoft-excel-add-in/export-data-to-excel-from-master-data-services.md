---
title: マスター データ サービスから Excel へのデータのエクスポート | Microsoft Docs
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: dd29389b-928c-4e50-995c-c6af27f97805
caps.latest.revision: 16
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 3eb6242e6e6063e5c3b531e44afccb21ed964637
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35403284"
---
# <a name="export-data-to-excel-from-master-data-services"></a>マスター データ サービスから Excel へのデータのエクスポート

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]では、データを使用するには、MDS リポジトリからデータをエクスポートする必要があります。  
  
 読み込み前にデータセットをフィルター処理する場合は、「[エクスポート前のデータのフィルター処理 (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/filter-data-before-exporting-mds-add-in-for-excel.md)」を参照してください。  
  
## <a name="prerequisites"></a>Prerequisites  
 この手順を実行するには  
  
-   **[エクスプローラー]** 機能領域にアクセスする権限が必要です。  
  
### <a name="to-export-data-from-mds-into-excel"></a>MDS から Excel にデータをエクスポートするには  
  
1.  Excel を開いて、**[マスター データ]** タブで MDS リポジトリに接続します。 詳細については、「[MDS リポジトリへの接続 (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md)」を参照してください。  
  
2.  **[マスター データ エクスプローラー]** ペインで、モデルおよびバージョンを選択します。 エンティティの一覧が作成されます。  
  
    -   **[マスター データ エクスプローラー]** ペインが表示されない場合は、 **[接続と読み込み]** グループの **[エクスプローラーの表示]** をクリックします。  
  
    -   **[マスター データ エクスプローラー]** ペインが無効になっている場合は、既存のシートに MDS によって管理されるデータが既に含まれています。 ペインを有効にするには、新しいワークシートを開きます。  
  
3.  **[マスター データ エクスプローラー]** ペインのエンティティの一覧で、読み込むエンティティをダブルクリックします。  
  
    > [!NOTE]  
    >  -   最初の 100 万個のメンバーだけが Excel に読み込まれます。 読み込む前に一覧をフィルター処理するには、リボンの **[接続と読み込み]** グループで、 **[フィルター]** をクリックします。  
    > -   制約リスト (ドメイン ベースの属性) の列では、既定で最初の 25,000 個の値だけが読み込まれます。 この数値は、Excel がインストールされているコンピューターにある、excelusersettings.config ファイルの MaximumDbaEntitySize プロパティで変更できます。 このファイルは C:\Users\\<ユーザー\>\AppData\Local\Microsoft\Microsoft SQL Server\130\MasterDataServices\\ にあります。  
    >   
    >      ドメイン ベースの属性に MaximumDbEntitySize プロパティの設定値を超えている値の数がある場合は、値の一覧は読み込まれません。  
  
    > [!NOTE]  
    >  32 ビットの Excel で Microsoft Excel 用アドインを使用して、テキスト区切りのデータを読み込み、 **[ロードするセル数]** プロパティと **[パブリッシュするセル数]** プロパティの設定が両方とも最大値の 1000 に設定されている場合、メモリ不足エラーが発生します。 **[ロードするセル数]** および **[パブリッシュするセル数]** に最大値を設定するには、64 ビットの Excel を使用する必要があります。  
  
## <a name="next-steps"></a>Next Steps  
 [Excel からマスター データ サービスにデータをインポートする (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>参照  
 [概要: Excel へのデータのエクスポート (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [[フィルター] ダイアログ ボックス (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md)   
 [概要: Excel からのデータのインポート (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
