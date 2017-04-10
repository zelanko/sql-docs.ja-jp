---
title: "モデル権限とメンバー権限の重複 (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "モデル [マスター データ サービス], 有効な権限"
  - "権限 [マスター データ サービス], モデルとメンバーの重複"
  - "メンバー [マスター データ サービス], 有効な権限"
ms.assetid: 9fd7a555-43bf-4796-a8b6-1ca63a291216
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# モデル権限とメンバー権限の重複 (Master Data Services)
  メンバーに割り当てられている権限は、モデル オブジェクトに割り当てられている権限と重複している可能性があります。 重複が発生すると、より制限の厳しい権限が有効になります。  
  
 メンバーに割り当てられている権限が、対応するモデル オブジェクトの権限とは異なる場合、次のルールが適用されます。  
  
-   **拒否** が他のどの権限よりも優先されます。  
  
-   **Admin** モデル レベルのアクセス許可は、他のすべてのアクセス許可を上書きし、下位レベルのアクセス許可をすべて (CRUD) に変更されます。  
  
-   有効なアクセス権限は、メンバーと属性のアクセス権限と交差します。  
  
     たとえば、メンバーの権限に **作成** と **更新**が含まれる場合、属性の権限は **更新**になります。 有効な権限は **更新**です。  
  
 次の図は、属性の権限がメンバーの権限とは異なる場合に、個々の属性値に対して有効な権限を示しています。  
  
 ![mds_conc_security_member_overlap_table](../master-data-services/media/mds-conc-security-member-overlap-table.gif "mds_conc_security_member_overlap_table")  
  
## 例 1  
 ![mds_conc_overlap_model_1](../master-data-services/media/mds-conc-overlap-model-1.gif "mds_conc_overlap_model_1")  
  
 **[モデル]** タブで、Product エンティティに **更新** 権限が割り当てられています。 エンティティのすべての属性がこの権限を継承しています。  
  
 **[階層メンバー]** タブで、派生階層の Mountain Bikes サブカテゴリ ノードに **更新** 権限が割り当てられています。  
  
 結果: **[エクスプローラー]**で、Mountain Bikes ノード内のすべてのメンバーについて、すべての属性値に対する **更新** 権限がユーザーに与えられます。 その他のメンバーと属性は、すべて非表示になります。  
  
 ![mds_conc_overlap_model_example_1](../master-data-services/media/mds-conc-overlap-model-example-1.gif "mds_conc_overlap_model_example_1")  
  
## 例 2  
 ![mds_conc_overlap_model_2](../master-data-services/media/mds-conc-overlap-model-2.gif "mds_conc_overlap_model_2")  
  
 **[モデル]** タブで、Subcategory 属性に **更新** 権限が割り当てられています。  
  
 **[階層メンバー]** タブで、派生階層の Mountain Bikes サブカテゴリ ノードに **読み取り** 権限が明示的に割り当てられています。  
  
 結果: **[エクスプローラー]**で、Mountain Bikes ノード内のメンバーについて、Subcategory 属性値に対する **読み取り** 権限がユーザーに与えられます。 その他のメンバーと属性は、すべて非表示になります。  
  
 ![mds_conc_overlap_model_example_2](../master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")  
  
## 例 3  
 ![mds_conc_overlap_model_3](../master-data-services/media/mds-conc-overlap-model-3.gif "mds_conc_overlap_model_3")  
  
 **[モデル]** タブで、Subcategory 属性に **読み取り** 権限が割り当てられています。  
  
 **[階層メンバー]** タブで、派生階層の Mountain Bikes サブカテゴリに **更新** 権限が明示的に割り当てられています。  
  
 結果: **[エクスプローラー]**で、属性値に対する **読み取り** 権限がユーザーに与えられます。 その他のメンバーと属性は、すべて非表示になります。  
  
 ![mds_conc_overlap_model_example_2](../master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")  
  
## 参照  
 [アクセス許可を決定する方法と #40 です。マスター データ サービスと #41 です。](../master-data-services/how-permissions-are-determined-master-data-services.md)   
 [重複するユーザーとグループのアクセス許可と #40 です。マスター データ サービスと #41 です。](../master-data-services/overlapping-user-and-group-permissions-master-data-services.md)  
  
  