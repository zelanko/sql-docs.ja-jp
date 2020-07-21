---
title: 階層メンバーのアクセス許可 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- members [Master Data Services], permissions
- permissions [Master Data Services], members
ms.assetid: b3880eed-1bf6-4f65-ab23-b08c194cc858
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a8a50ce407e0f9284d07a7248f08decacf434fee
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971412"
---
# <a name="hierarchy-member-permissions-master-data-services"></a>階層メンバーの権限 (マスター データ サービス)
  階層メンバーの権限はオプションであり、特定のメンバーに対するユーザーのアクセスを制限する場合にのみ使用します。 **[階層メンバー]** タブで権限を割り当てていなければ、ユーザーの権限は、 **[モデル]** タブで割り当てられた権限のみに基づいて決定されます。  
  
 階層メンバーの権限は、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ユーザーインターフェイス (UI) の [**ユーザー/グループの権限**] 機能領域の [**階層メンバー** ] タブで割り当てられます。これらのアクセス許可によって、ユーザーが UI の [**エクスプローラー** ] 機能領域でアクセスできるメンバーが決まります。  
  
 **[階層メンバー]** タブでは、各階層がツリー構造として表されます。 ツリー内のノードに権限を割り当てると、下位レベルで権限が明示的に割り当てられていない限り、すべての子がその権限を継承します。  
  
> [!NOTE]  
>  階層内のいずれかのノードに権限を割り当てると、同じレベル以上にある、それ以外のノード内のメンバーはすべて暗黙的に拒否されます。  
  
 **[エクスプローラー]** では、メンバーが表示されるすべての領域にメンバー権限が適用されます。 たとえば、**読み取り**専用権限を持つメンバーは、属しているすべてのエンティティ、階層、およびコレクションで読み取り専用になります。  
  
 階層メンバーの権限は、それらを割り当てたモデル バージョンと、そのバージョンの以降のコピーに適用されます。 割り当てたバージョンよりも前のバージョンには適用されません。  
  
|権限|説明|  
|----------------|-----------------|  
|**読み取り専用**|メンバーが表示されますが、ユーザーはメンバーを変更できません。 また、メンバーが属する明示的階層またはコレクションでメンバーを移動することもできません。<br /><br /> 注:**読み取り**専用権限を**ルート**に割り当てた場合、**ルート**の下のメンバーは読み取り専用になります。ただし、明示的階層およびコレクションでは、ユーザーはメンバーを**ルート**に移動し、新しいメンバーを**ルート**に追加できます。|  
|**Update**|メンバーが表示され、ユーザーはメンバーを変更できます。 また、メンバーが属する明示的階層またはコレクションでメンバーを移動することもできます。|  
|**Deny**|メンバーが表示されません。|  
  
 **[階層メンバー]** タブでは、権限を割り当ててもすぐには有効になりません。 権限が適用される頻度は、 **データベースの System Settings テーブルの** [メンバーのセキュリティ処理間隔の設定] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] の値に応じて異なります。 メンバー権限を直ちに適用するには、「 [メンバー権限を直ちに適用する (マスター データ サービス)](immediately-apply-member-permissions-master-data-services.md)に追加したりできます。  
  
> [!NOTE]  
>  階層メンバーの権限は、再帰型階層、明示的なキャップを持つ派生階層、およびレベルを非表示にした階層に割り当てることはできません。  
  
## <a name="possible-overlapping-permissions"></a>重複の可能性がある権限  
 メンバーに権限を割り当てる際、権限の重複を解決することが必要になる場合があります。  
  
### <a name="when-a-member-belongs-to-multiple-hierarchies"></a>1 つのメンバーが複数の階層に属している場合  
 複数の階層に同じメンバーを含めることができます。  
  
-   ある階層ノードに**更新**権限が割り当てられていて、別の階層ノードが**読み取り**専用に割り当てられている場合、ノード内のメンバーは**読み取り**専用になります。  
  
-   1つの階層ノードに**更新**権限または**読み取り専用**権限が割り当てられていて、別のノードに [**拒否**] が割り当てられている場合、ノード内のメンバーは表示されません。  
  
## <a name="see-also"></a>参照  
 [階層メンバーの権限を割り当てる &#40;マスターデータサービス&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [アクセス許可の決定方法 &#40;マスターデータサービス&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md)   
 [メンバー &#40;マスターデータサービス&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [階層 &#40;マスターデータサービス&#41;](../../2014/master-data-services/hierarchies-master-data-services.md)   
 [メンバー権限を直ちに適用する (マスター データ サービス)](immediately-apply-member-permissions-master-data-services.md)  
  
  
