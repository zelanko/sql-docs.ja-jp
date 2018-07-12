---
title: Level 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 41235402-bb9e-4cb7-b91e-431e77db19cf
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 027ccec12f08efddc9b48c56ad7ed2f22ec5b15b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155753"
---
# <a name="level-function-report-builder-and-ssrs"></a>Level 関数 (レポート ビルダーおよび SSRS)
  再帰型階層の現在の深さのレベルを返します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>構文  
  
```  
  
Level(scope)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *スコープ (scope)*  
 (`String`) (省略可)。 集計関数の適用先となるレポート アイテムを含むデータセット、グループ、またはデータ領域の名前です。 *scope* を指定しない場合、現在のスコープが使用されます。  
  
## <a name="return-type"></a>戻り値の型  
 返します、`Integer`します。 場合*スコープ*をデータセットまたはデータ領域を指定しますまたは、再帰的でないグループを指定します (グループ化なしでは、`Parent`要素)、 `Level` 0 を返します。 *scope* を指定しない場合は、現在のスコープのレベルが返されます。  
  
## <a name="remarks"></a>コメント  
 `Level` 関数から返される値は、0 を基準にしています。つまり、階層の最初のレベルは 0 です。  
  
 `Level` 関数は、従業員一覧などの再帰型階層にインデントを付けるために使用できます。  
  
 再帰的型階層については、「[複数の再帰型階層グループの作成 &#40;レポート ビルダーおよび SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="example"></a>例  
 次のコード例では、Employees グループの行のレベルが返されます。  
  
```  
=Level("Employees")  
```  
  
## <a name="see-also"></a>参照  
 [レポートで式を使用して&#40;レポート ビルダーおよび SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [合計、集計、および組み込みコレクションの式のスコープ&#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
