---
title: "メンバー (マスター データ サービス) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "リーフ メンバー [Master Data Services]"
  - "統合メンバー [マスター データ サービス]"
  - "統合メンバー [マスター データ サービス], 統合メンバーについて"
  - "メンバー [Master Data Services] メンバーについて"
  - "リーフ メンバー [Master Data Services] リーフ メンバーについて"
  - "メンバー [Master Data Services]"
ms.assetid: 0fda32b9-677d-4ba2-bb28-f76f2383a30f
caps.latest.revision: 16
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 14
---
# メンバー (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] では、メンバーは物理マスター データです。 たとえば、Product エンティティの Road-150 バイクや、Customer エンティティの特定の顧客をメンバーにすることができます。  
  
## メンバーと他のモデル オブジェクトの関連付け  
 メンバーは、テーブルの行と考えることができます。 関連するメンバーはエンティティに含まれ、各メンバーは属性値によって定義されます。  
  
 この例では、テーブルはエンティティを、テーブルの行はメンバーを、テーブルの列は属性を、それぞれ表しています。 各セルは特定のメンバーの属性値を表します。  
  
 ![テーブルとして表されたマスター データ サービス エンティティ](../master-data-services/media/mds-conc-entity-table.gif "テーブルとして表されたマスター データ サービス エンティティ")  
  
## メンバーの種類  
 メンバーには、リーフ メンバー、統合メンバー、およびコレクション メンバーという 2 種類があります。  
  
 リーフ メンバーは、エンティティの既定のメンバーです。  
  
-   派生階層では、リーフ メンバーは唯一の種類のメンバーです。 1 つのエンティティのリーフ メンバーは、別のエンティティのリーフ メンバーの親として使用されます。  
  
-   明示的階層では、リーフ メンバーは最下位レベルで、子を持つことができません。  
  
 統合メンバーは、エンティティの明示的階層およびコレクションが有効になっているときにのみ存在します。  
  
-   派生階層には、統合メンバーは含まれません。  
  
-   明示的階層では、統合メンバーは階層内の他のメンバーの親になることも、子になることもできます。  
  
## 階層とコレクションを使用したメンバーの整理  
 階層およびコレクションを使用して、レポートまたは分析のためにメンバーをグループ化できます。 詳細については、「[階層 (マスター データ サービス)](../master-data-services/hierarchies-master-data-services.md)」および「[コレクション (マスター データ サービス)](../master-data-services/collections-master-data-services.md)」を参照してください。  
  
## メンバーの例  
 次の例では、各メンバーは、Name、Code、Subcategory、StandardCost、ListPrice、および FilePhoto という属性値で構成されています。  
  
 ![自転車製品エンティティ テーブル](../master-data-services/media/mds-conc-entity-table-w-data.gif "自転車製品エンティティ テーブル")  
  
## 関連タスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|新しいリーフ メンバーを作成する。|[リーフ メンバーを作成する (マスター データ サービス)](../master-data-services/create-a-leaf-member-master-data-services.md)|  
|新しい統合メンバーを作成する。|[統合メンバーを作成する (マスター データ サービス)](../master-data-services/create-a-consolidated-member-master-data-services.md)|  
|既存のメンバーまたはコレクションを削除する。|[メンバーまたはコレクションを削除する (マスター データ サービス)](../master-data-services/delete-a-member-or-collection-master-data-services.md)|  
|削除したメンバーまたはコレクションを再アクティブ化する。|[メンバーまたはコレクションを再アクティブ化する (マスター データ サービス)](../master-data-services/reactivate-a-member-or-collection-master-data-services.md)|  
|メンバーの属性値を更新する。|[属性の型の変更 (Excel 用 MDS アドイン)](../master-data-services/microsoft-excel-add-in/change-the-attribute-type-mds-add-in-for-excel.md)|  
|階層内のメンバーを移動する。|[階層内のメンバーを移動する (マスター データ サービス)](../Topic/Move%20Members%20within%20a%20Hierarchy%20\(Master%20Data%20Services\).md)|  
|マージの競合を解決する。|[競合のマージ (マスター データ サービス)](../master-data-services/merge-conflicts-master-data-services.md)|  
  
## 関連コンテンツ  
  
-   [マスター データ サービスの概要 (MDS)](../master-data-services/master-data-services-overview-mds.md)  
  
-   [エンティティ (マスター データ サービス)](../master-data-services/entities-master-data-services.md)  
  
-   [属性 (マスター データ サービス)](../master-data-services/attributes-master-data-services.md)  
  
-   [階層 (マスター データ サービス)](../master-data-services/hierarchies-master-data-services.md)  
  
-   [コレクション (マスター データ サービス)](../master-data-services/collections-master-data-services.md)  
  
-   [リーフ権限 (マスター データ サービス)](../master-data-services/leaf-permissions-master-data-services.md)  
  
-   [統合権限 (マスター データ サービス)](../Topic/Consolidated%20Permissions%20\(Master%20Data%20Services\).md)  
  
-   [フィルター演算子 (マスター データ サービス)](../master-data-services/filter-operators-master-data-services.md)  
  
  