---
title: (レポート ビルダーおよび SSRS) の再帰型階層グループの作成 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 92412bbde8a1032b34264ca254560f31704281e8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63135580"
---
# <a name="creating-recursive-hierarchy-groups-report-builder-and-ssrs"></a>(レポート ビルダーおよび SSRS) の再帰型階層グループの作成
  親と子間のリレーションシップがデータセット内のフィールドで表される再帰型データを表示するのには、子フィールドに基づいたデータ領域グループ式を設定し、親フィールドに基づいた親プロパティを設定します。  
  
 再帰型階層グループ、組織のグラフ内の従業員などの一般的な用途は、階層データを表示します。 データセットには、従業員とマネージャー、場所も管理者の名前が従業員の一覧に表示の一覧が含まれています。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="creating-recursive-hierarchies"></a>再帰型階層を作成します。  
 Tablix データ領域で再帰型階層を構築するには、子のデータと、親データを指定するフィールドにグループの親プロパティを指定するフィールドにグループ式を設定する必要があります。 たとえば、従業員 ID とマネージャーに Parent プロパティをマネージャー、従業員のレポートがグループ式を設定、従業員 ID およびマネージャー ID のフィールドを含むデータセット id。  
  
 再帰型階層 (親プロパティを使用するグループ) として定義されているグループには、1 つだけのグループ式を設定できます。 テキスト ボックスの余白に `Level` 関数を使用して、階層内のレベルに応じて従業員名をインデントできます。  
  
 詳細については、次を参照してください。[を追加またはデータ領域でグループを削除する&#40;レポート ビルダーおよび SSRS&#41; ](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)と[再帰型階層グループの作成&#40;レポート ビルダーおよび SSRS&#41;](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md)します。  
  
### <a name="aggregate-functions-that-support-recursion"></a>再帰をサポートする集計関数  
 パラメーターを受け取る Reporting Services 集計関数を使用する*再帰*再帰型階層の集計データを計算します。 次の関数が受け入れる`Recursive`をパラメーターとして。[合計](report-builder-functions-sum-function.md)、 [Avg](report-builder-functions-avg-function.md)、[カウント](report-builder-functions-count-function.md)、 [CountDistinct](report-builder-functions-countdistinct-function.md)、 [CountRows](report-builder-functions-countrows-function.md)、[最大](report-builder-functions-max-function.md)、 [Min](report-builder-functions-min-function.md)、 [StDev](report-builder-functions-stdev-function.md)、 [StDevP](report-builder-functions-stdevp-function.md)、[合計](report-builder-functions-sum-function.md)、 [Var](report-builder-functions-var-function.md)、および[VarP](report-builder-functions-varp-function.md). 詳細については、「 [集計関数リファレンス (レポート ビルダーおよび SSRS)](report-builder-functions-aggregate-functions-reference.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [テーブル、マトリックス、および一覧&#40;レポート ビルダーおよび SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Tablix データ領域 &#40;レポート ビルダーおよび SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [集計関数リファレンス&#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)   
 [テーブル &#40;レポート ビルダーおよび SSRS&#41;](tables-report-builder-and-ssrs.md)   
 [マトリックス &#40;レポート ビルダーおよび SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)   
 [一覧 &#40;レポート ビルダーおよび SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
