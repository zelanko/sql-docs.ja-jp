---
title: 複数の再帰型階層グループの作成 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 52410faf7827c6692575aff641070565d0ef6243
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177255"
---
# <a name="creating-recursive-hierarchy-groups-report-builder-and-ssrs"></a>複数の再帰型階層グループの作成 (レポート ビルダーおよび SSRS)
  親と子間のリレーションシップがデータセット内のフィールドで表される再帰的なデータを表示するには、子フィールドに基づくデータ領域グループ式を設定し、親フィールドに基づく親プロパティを設定することができます。  
  
 階層データの表示は、組織図に含まれている従業員など、再帰型階層グループでよく使用されます。 データセットには従業員とマネージャーの一覧が含まれており、マネージャー名は従業員の一覧にも表示されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="creating-recursive-hierarchies"></a>再帰型階層の作成  
 Tablix データ領域で再帰型階層を作成するには、子データを指定するフィールドにグループ式を設定し、親データを指定するフィールドにグループの親プロパティを設定する必要があります。 たとえば、従業員がマネージャーの監督下にある場合、従業員 ID およびマネージャー ID のフィールドを含んでいるデータセットでは、グループ式を従業員 ID に設定し、親プロパティをマネージャー ID に設定します。  
  
 再帰型階層として定義されたグループ (親プロパティを使用しているグループ) には、グループ式は 1 つしか設定できません。 テキスト ボックスの余白に `Level` 関数を使用して、階層内のレベルに応じて従業員名をインデントできます。  
  
 詳細については、「[データ領域でのグループの追加または削除 &#40;レポート ビルダーおよび SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)」と「[再帰型階層グループの作成 &#40;レポート ビルダーおよび SSRS&#41;](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md)」を参照してください。  
  
### <a name="aggregate-functions-that-support-recursion"></a>再帰をサポートする集計関数  
 パラメーター *Recursive* を受け取る Reporting Services 集計関数を使用して、再帰型階層の集計データを計算できます。 The following functions accept `Recursive` as a parameter: [Sum](report-builder-functions-sum-function.md), [Avg](report-builder-functions-avg-function.md), [Count](report-builder-functions-count-function.md), [CountDistinct](report-builder-functions-countdistinct-function.md), [CountRows](report-builder-functions-countrows-function.md), [Max](report-builder-functions-max-function.md), [Min](report-builder-functions-min-function.md), [StDev](report-builder-functions-stdev-function.md), [StDevP](report-builder-functions-stdevp-function.md), [Sum](report-builder-functions-sum-function.md), [Var](report-builder-functions-var-function.md), and [VarP](report-builder-functions-varp-function.md). 詳細については、「 [集計関数リファレンス (レポート ビルダーおよび SSRS)](report-builder-functions-aggregate-functions-reference.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Tablix データ領域 &#40;レポート ビルダーおよび SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [集計関数リファレンス&#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)   
 [テーブル &#40;レポート ビルダーおよび SSRS&#41;](tables-report-builder-and-ssrs.md)   
 [マトリックス &#40;レポート ビルダーおよび SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)   
 [一覧 &#40;レポート ビルダーおよび SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  