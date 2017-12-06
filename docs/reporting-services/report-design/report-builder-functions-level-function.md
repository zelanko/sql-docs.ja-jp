---
title: "Level 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-design
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41235402-bb9e-4cb7-b91e-431e77db19cf
caps.latest.revision: "7"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 5ed59cf792bb62b1930ce3bcf6cf9ea0e505b028
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="report-builder-functions---level-function"></a>レポート ビルダー関数 - Level 関数
  再帰型階層の現在の深さのレベルを返します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>構文  
  
```  
  
Level(scope)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *スコープ (scope)*  
 (**String**) (省略可)。 集計関数の適用先となるレポート アイテムを含むデータセット、グループ、またはデータ領域の名前です。 *scope* を指定しない場合、現在のスコープが使用されます。  
  
## <a name="return-type"></a>戻り値の型  
 **Integer**値を返します。 *scope* にデータセットまたはデータ領域を指定した場合や、再帰的でないグループ ( **Parent** 要素を持たないグループ) を指定した場合、 **Level** は 0 を返します。 *scope* を指定しない場合は、現在のスコープのレベルが返されます。  
  
## <a name="remarks"></a>解説  
 **Level** 関数から返される値は、0 を基準にしています。つまり、階層の最初のレベルは 0 です。  
  
 **Level** 関数は、従業員一覧などの再帰型階層にインデントを付けるために使用できます。  
  
 再帰的型階層については、「[複数の再帰型階層グループの作成 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="example"></a>例  
 次のコード例では、Employees グループの行のレベルが返されます。  
  
```  
=Level("Employees")  
```  
  
## <a name="see-also"></a>参照  
 [レポートでの式の使用 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [式の例 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
