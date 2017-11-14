---
title: "Count プロパティ (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Collection::Count
helpviewer_keywords:
- Count property [ADO]
ms.assetid: da9ccd1f-d402-41a2-940c-45556fc5340d
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 173b2fc9073676e77ad3068e9e9dc3ca76089702
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="count-property-ado"></a>Count プロパティ (ADO)
コレクション内のオブジェクトの数を示します。  
  
## <a name="return-value"></a>戻り値  
 返します、**長い**値。  
  
## <a name="remarks"></a>解説  
 使用して、**カウント**プロパティを指定したコレクション内のオブジェクトの数を調べる。  
  
 コレクションのメンバーの番号付けは 0 から始まるため、する必要がありますループ常に 0 から始まるの値で終わる、**カウント**から 1 を引いたプロパティです。 Microsoft Visual Basic を使用しているし、確認せずにコレクションのメンバーをループ処理する場合、**カウント**プロパティを使用して、**ごとにしています.[次へ]**コマンド。  
  
 場合、**カウント**プロパティが 0 で、コレクションにオブジェクトがありません。  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[Axes コレクション (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[Columns コレクション (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[CubeDefs コレクション (ADO MD)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[Dimensions コレクション (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[Errors コレクション (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)|[Fields コレクション (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[グループのコレクション (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Hierarchies コレクション (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[Indexes コレクション (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[キーのコレクション (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)|[Levels コレクション (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[メンバーのコレクション (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[Parameters コレクション (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)|[位置コレクション (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[プロシージャのコレクション (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|[プロパティのコレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)|[テーブル コレクション (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|[ユーザー コレクション (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[ビューのコレクション (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>参照  
 [Count プロパティの例 (VB)](../../../ado/reference/ado-api/count-property-example-vb.md)   
 [Count プロパティの例 (vc++)](../../../ado/reference/ado-api/count-property-example-vc.md)   
 [Refresh メソッド (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)

