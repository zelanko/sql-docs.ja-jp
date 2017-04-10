---
title: "データの結合 (Excel 用 MDS アドイン) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a867dc15-5a0d-457c-8304-ac323bcf9377
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# データの結合 (Excel 用 MDS アドイン)
   [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], 、発行する前にデータを比較する場合に、2 つのワークシートのデータを結合します。 この手順では、2 つのワークシートのデータを 1 つに結合します。 これにより、さらに比較を実行して、MDS リポジトリにパブリッシュするデータを決定することができます。  
  
## 前提条件  
  
-   MDS によって管理されるデータが含まれているワークシートが必要です。 詳細については、次を参照してください。 [マスター データ サービスから Excel にデータのエクスポート](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)します。  
  
-   MDS によって管理されるデータに結合するデータが含まれているワークシートが必要です。 このシートには、ヘッダー行が必要です。  
  
### MDS によって管理されるシートに管理されないデータを結合するには  
  
1.  MDS によって管理されるデータを格納しているシートで、 **パブリッシュと検証** グループで、[ **データの結合**します。  
  
2.   **データの結合** ] ダイアログ ボックスの横に、 **MDS データと結合する範囲** テキスト ボックスで、アイコンをクリックします。 ダイアログ ボックスが縮小されます。  
  
3.  結合するデータを含むシートをクリックします。  
  
4.  シート上の結合するすべてのセル (ヘッダー行を含む) を強調表示します。  
  
5.   **データの結合** ] ダイアログ ボックスで、アイコンをクリックします。 ダイアログ ボックスが拡張されます。  
  
6.  [MDS エンティティの下にある列に示された列の **対応する列**です。 すべての MDS 列に対応する列が必要なわけではありません。  
  
7.  クリックして **結合**です。 A **ソース** データが MDS または外部ソースからかどうかを示す列が表示されます。  
  
## 次の手順  
  
-   MDS によって管理されると、外部データの類似点を検索するには、次を参照してください。 [のようなデータの照合と #40 です。MDS アドイン Excel & #41;](../../master-data-services/microsoft-excel-add-in/match-similar-data-mds-add-in-for-excel.md)です。  
  
## 参照  
 [概要: Excel と #40; へのデータのエクスポートMDS アドイン Excel & #41 です。](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Excel 用 MDS アドインでのデータ品質照合](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)  
  
  