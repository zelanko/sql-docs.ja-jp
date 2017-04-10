---
title: "(MDS アドイン Excel 用) にエクスポートする前にデータのフィルター | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9e30eae0-776b-4a09-aac3-0c0249d92ca5
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 10
---
# (MDS アドイン Excel 用) にエクスポートする前にデータのフィルター
   [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], 、サイズまたは Excel にエクスポートするデータのスコープを制限する場合に、データをフィルター処理します。  
  
## 前提条件  
 この手順を実行するには  
  
-   **[エクスプローラー]** 機能領域にアクセスする権限が必要です。  
  
### エクスポートする前にデータをフィルター処理するには  
  
1.  Excel を起動し、[、 **マスター データ** ] タブで、MDS リポジトリに接続します。 詳細については、次を参照してください [MDS リポジトリと #40; への接続。MDS アドイン Excel & #41;](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md)します。  
  
2.   **マスター データ エクスプ ローラー** ] ウィンドウで、モデルおよびバージョンを選択します。 エンティティの一覧が作成されます。  
  
    -   場合、 **マスター データ エクスプ ローラー** ペインが表示されていない、 **接続と読み込み** グループで、[ **[エクスプ ローラーの**です。  
  
    -   場合、 **マスター データ エクスプ ローラー** ウィンドウが無効になっている、既存のシートには既に MDS によって管理されるデータが含まれているためにです。 ペインを有効にするには、新しいワークシートを開きます。  
  
3.   **マスター データ エクスプ ローラー** ウィンドウ、エンティティの一覧で、エンティティのフィルターを適用する] をクリックします。  
  
4.  リボンで、 **接続と読み込み** グループで、[ **フィルター**します。  
  
5.  完了、 **フィルター** ] ダイアログ ボックスを表示する属性 (列) を選択すると、列の順序の設定と必要な場合、データのフィルター処理より少ない行が返されるようにします。 ビュー、 **概要** ペインのデータの量が返されます。 詳細については、次を参照してください。 [フィルター] ダイアログ ボックスと #40 です。MDS アドイン Excel & #41;](../Topic/Filter%20Dialog%20Box%20\(MDS%20Add-in%20for%20Excel\).md)します。  
  
6.  クリックして **データを読み込む**です。 シートに MDS によって管理されるデータが入力されます。  
  
    > [!NOTE]  
    >  -   最初の 100 万個のメンバーだけが Excel に読み込まれます。  
    > -   制約リスト (ドメイン ベースの属性) の列では、既定で最初の 25,000 個の値だけが読み込まれます。  
  
## 次の手順  
 [マスター データ サービスおよび #40;] に、Excel からデータをインポートします。MDS アドイン Excel & #41 です。](../Topic/Import%20Data%20from%20Excel%20to%20Master%20Data%20Services%20\(MDS%20Add-in%20for%20Excel\).md)  
  
## 参照  
 [概要: Excel と #40; へのデータのエクスポートMDS アドイン Excel & #41 です。](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [フィルター] ダイアログ ボックスと #40 です。MDS アドイン Excel & #41 です。](../Topic/Filter%20Dialog%20Box%20\(MDS%20Add-in%20for%20Excel\).md)   
 [並べ替え列と #40 です。MDS アドイン Excel & #41 です。](../../master-data-services/microsoft-excel-add-in/reorder-columns-mds-add-in-for-excel.md)  
  
  