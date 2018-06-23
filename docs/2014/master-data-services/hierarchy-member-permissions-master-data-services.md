---
title: 階層メンバーのアクセス許可 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- members [Master Data Services], permissions
- permissions [Master Data Services], members
ms.assetid: b3880eed-1bf6-4f65-ab23-b08c194cc858
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: e5ac17b8e72209a25c1e8e213d775012e800ca35
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083005"
---
# <a name="hierarchy-member-permissions-master-data-services"></a>階層メンバーの権限 (マスター データ サービス)
  階層メンバーの権限はオプションであり、特定のメンバーに対するユーザーのアクセスを制限する場合にのみ使用します。 **[階層メンバー]** タブで権限を割り当てていなければ、ユーザーの権限は、 **[モデル]** タブで割り当てられた権限のみに基づいて決定されます。  
  
 階層メンバーの権限は、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のユーザー インターフェイス (UI) を使用して、 **[ユーザー/グループの権限]** 機能領域の **[階層メンバー]** タブで割り当てられます。これらの権限によって、UI の **[エクスプローラー]** 機能領域でユーザーがアクセスできるメンバーが決まります。  
  
 **[階層メンバー]** タブでは、各階層がツリー構造として表されます。 ツリー内のノードに権限を割り当てると、下位レベルで権限が明示的に割り当てられていない限り、すべての子がその権限を継承します。  
  
> [!NOTE]  
>  階層内のいずれかのノードに権限を割り当てると、同じレベル以上にある、それ以外のノード内のメンバーはすべて暗黙的に拒否されます。  
  
 **[エクスプローラー]** では、メンバーが表示されるすべての領域にメンバー権限が適用されます。 メンバーなど、**読み取り専用**権限は、エンティティ、階層、およびコレクションが属するで読み取り専用です。  
  
 階層メンバーの権限は、それらを割り当てたモデル バージョンと、そのバージョンの以降のコピーに適用されます。 割り当てたバージョンよりも前のバージョンには適用されません。  
  
|権限|説明|  
|----------------|-----------------|  
|**読み取り専用です。**|メンバーが表示されますが、ユーザーはメンバーを変更できません。 また、メンバーが属する明示的階層またはコレクションでメンバーを移動することもできません。<br /><br /> 注: を割り当てる場合**読み取り専用**するアクセス許可**ルート**、下にあるメンバー**ルート**読み取り専用ですただし、明示的階層およびコレクションで、ユーザーが移動できる。メンバーを**ルート**に新しいメンバーを追加したりできます**ルート**です。|  
|**Update**|メンバーが表示され、ユーザーはメンバーを変更できます。 また、メンバーが属する明示的階層またはコレクションでメンバーを移動することもできます。|  
|**Deny**|メンバーが表示されません。|  
  
 **[階層メンバー]** タブでは、権限を割り当ててもすぐには有効になりません。 権限が適用される頻度は、 **データベースの System Settings テーブルの** [メンバーのセキュリティ処理間隔の設定] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] の値に応じて異なります。 メンバー権限を直ちに適用するには、「[メンバー権限を直ちに適用する方法 (マスター データ サービス)](immediately-apply-member-permissions-master-data-services.md)」を参照してください。  
  
> [!NOTE]  
>  階層メンバーの権限は、再帰型階層、明示的なキャップを持つ派生階層、およびレベルを非表示にした階層に割り当てることはできません。  
  
## <a name="possible-overlapping-permissions"></a>重複の可能性がある権限  
 メンバーに権限を割り当てる際、権限の重複を解決することが必要になる場合があります。  
  
### <a name="when-a-member-belongs-to-multiple-hierarchies"></a>1 つのメンバーが複数の階層に属している場合  
 複数の階層に同じメンバーを含めることができます。  
  
-   1 つの階層ノードに割り当てられている場合**更新**アクセス許可が割り当てられている**読み取り専用**、ノード内のメンバーは**読み取り専用**です。  
  
-   1 つの階層ノードに割り当てられている場合**更新**または**読み取り専用**権限と別のノードが割り当てられている**Deny**ノード内のメンバーは表示されません。  
  
## <a name="see-also"></a>参照  
 [階層メンバー権限を割り当てる&#40;マスター データ サービス&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [権限の決定方法&#40;マスター データ サービス&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md)   
 [メンバー (マスター データ サービス)](../../2014/master-data-services/members-master-data-services.md)   
 [階層 (マスター データ サービス)](../../2014/master-data-services/hierarchies-master-data-services.md)   
 [メンバーの権限を直ちに適用&#40;マスター データ サービス&#41;](immediately-apply-member-permissions-master-data-services.md)  
  
  