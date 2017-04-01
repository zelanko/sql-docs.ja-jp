---
title: "列の並べ替え (Excel 用 MDS アドイン) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ac00462e-c0f7-4b8d-86f2-d9eda2598a15
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# 列の並べ替え (Excel 用 MDS アドイン)
   [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], 、読み込みの前に、の一覧をフィルター処理して列の順序を変更することができます。  
  
 内の属性の順序を変更するときに、 **フィルター** ] ダイアログ ボックスで、データが Excel には新しい順序で読み込まれます。 しかし、次にその属性データをフィルター処理すると、元のデザインの順序に戻ります。 順序を永続的に変更するには、管理者がで順序を変更する必要があります、 **システム管理** マスター データ マネージャーの領域です。 詳細については、次を参照してください。 [属性の順序を変更する](../../master-data-services/change-the-order-of-attributes.md)です。  
  
## 前提条件  
 この手順を実行するには  
  
-   **[エクスプローラー]** 機能領域にアクセスする権限が必要です。  
  
### MDS によって管理される列を並べ替えるには  
  
1.  Excel を起動し、[、 **マスター データ** ] タブで、MDS リポジトリに接続します。 詳細については、次を参照してください [MDS リポジトリと #40; への接続。MDS アドイン Excel & #41;](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md)します。  
  
2.   **マスター データ エクスプ ローラー** ] ウィンドウで、モデルおよびバージョンを選択します。 エンティティの一覧が作成されます。  
  
    -   場合、 **マスター データ エクスプ ローラー** ペインが表示されていない、 **接続と読み込み** グループで、[ **Explorer を表示する**です。  
  
    -   場合、 **マスター データ エクスプ ローラー** ウィンドウが無効になっている、既存のシートには既に MDS によって管理されるデータが含まれているためにであります。 ペインを有効にするには、新しいワークシートを開きます。  
  
3.   **マスター データ エクスプ ローラー** ] ウィンドウで、エンティティをクリックします。  
  
4.   **接続と読み込み** グループで、[ **フィルター**します。  
  
5.   **フィルター** ダイアログ ボックスで、 **列** ] セクションの属性の一覧では、移動する属性をクリックします。  
  
6.  一覧の右側で、クリックして、 **を** または **ダウン** 属性を左右に移動し、ワークシート内にある矢印です。  
  
7.  ワークシート内で目的の順序 (左から右) となるまで、各属性について手順 7. を繰り返します。  
  
8.  クリックして **データを読み込む**です。 MDS によって管理されるデータがシートに入力され、指定した順序で列が表示されます。  
  
## 参照  
 [概要: Excel と #40; へのデータのエクスポートMDS アドイン Excel & #41 です。](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
  