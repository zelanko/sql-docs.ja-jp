---
title: "リーフ権限 (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "属性グループ [マスター データ サービス], 権限"
  - "メンバー [マスター データ サービス], リーフ メンバーの権限"
  - "権限 [マスター データ サービス], リーフ メンバー"
  - "リーフ メンバー [マスター データ サービス], 属性の権限"
  - "属性 [マスター データ サービス], リーフ メンバーの属性の権限"
ms.assetid: bde16e8c-bcd4-4041-8130-55c5450e5f72
caps.latest.revision: 9
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# リーフ権限 (Master Data Services)
  リーフ権限は、エンティティのすべてのリーフ メンバーの属性値に適用されます。  
  
 明示的階層が有効になっていないエンティティの場合、 **リーフ** への権限の割り当ては、エンティティへの権限の割り当てと同じです。  
  
 **注:**  
  
-   リーフ権限は、ユーザー インターフェイスの **[エクスプローラー]** 機能領域にのみ適用されます。  
  
-   **Name** 属性および **Code** 属性に割り当てられる権限は適用されません。  
  
|権限|Description|  
|----------------|-----------------|  
|**読み取り**|ユーザーはリーフ メンバーと属性を読み取ることができます。|  
|**作成**|ユーザーはリーフ メンバーを作成し、作成時に属性値を割り当てることができます。|  
|**更新**|ユーザーはリーフ メンバーと属性を更新できます。|  
|**Del**|ユーザーはリーフ メンバーを削除できます。|  
|**拒否**|リーフ メンバーに対するすべてのアクセスを拒否します。|  
  
 読み取り、作成、更新、削除の各権限は組み合わせることができます。 作成、更新、削除が割り当てられると、読み取り権限が自動的に割り当てられます。  
  
## 属性の権限  
 属性の権限は、特定のエンティティの属性の値に適用されます。 属性の権限のみを持つユーザーは、メンバーを追加または削除できません。  
  
|権限|Description|  
|----------------|-----------------|  
|**読み取り**|ユーザーは属性の読み取ることができます。|  
|**作成**|ユーザーはメンバーを作成するときに値を割り当てることができます。|  
|**Update**|ユーザーは属性を更新できます。|  
|**削除**|影響しません。|  
|**Deny**|属性が表示されません。<br /><br /> 注: Name 属性と Code 属性へのアクセスを明示的に拒否することはできません。|  
  
### 例  
 Product エンティティの場合、Subcategory 属性に **更新** 権限を割り当てます。 他のすべての属性に対しては権限を拒否します。  
  
|Name|コード|Subcategory (更新)|  
|----------|----------|----------------------------|  
|Mountain-100|BK-M101|\{5\} Mountain Bikes|  
|Mountain-100|BK-M201|\{5\} Mountain Bikes|  
  
 **[エクスプローラー]**では、Subcategory 列の属性値を更新できます。 属性に対する権限がない場合、その属性は表示されません。  
  
> [!NOTE]  
>  この例では、Subcategory は、SubcategoryList エンティティに基づくドメイン ベースの属性です。 Mountain-100 に対して別のサブカテゴリを選択することはできますが、SubcategoryList エンティティへのメンバーの追加または SubcategoryList エンティティからのメンバーの削除を行うことはできません。  
  
## 参照  
 [モデル オブジェクト権限を割り当てる (マスター データ サービス)](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [統合権限 (マスター データ サービス)](../Topic/Consolidated%20Permissions%20\(Master%20Data%20Services\).md)   
 [モデル オブジェクト権限 (マスター データ サービス)](../master-data-services/model-object-permissions-master-data-services.md)   
 [メンバー (マスター データ サービス)](../master-data-services/members-master-data-services.md)   
 [属性 (マスター データ サービス)](../master-data-services/attributes-master-data-services.md)  
  
  