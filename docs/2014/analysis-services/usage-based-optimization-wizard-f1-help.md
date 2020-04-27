---
title: 使用法に基づく最適化ウィザードの F1 ヘルプ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.usagebasedoptimizationwizard.f1
helpviewer_keywords:
- Usage-Based Optimization Wizard
ms.assetid: e5f5a938-ae7c-4f4e-9416-a7f94ac82763
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e5e94818245ba1e87d90f87539ae07e9531e5450
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66065568"
---
# <a name="usage-based-optimization-wizard-f1-help"></a>使用法に基づく最適化ウィザードの F1 ヘルプ
  使用法に基づく最適化ウィザードを使用するとパーティションの集計をデザインすることができ、その出力は集計のデザイン ウィザードに似ています。 ただし、使用法に基づく最適化ウィザードでは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスのクエリ ログに記録されているクエリの特定の使用パターンに基づいて集計をデザインします。 集計を使用すると、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]クエリごとに基になるデータソースのデータを再計算するのではなく、キューブストレージから事前計算済みの合計を直接取得できるため、パフォーマンスが向上します。  
  
 内[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]から使用法に基づく最適化ウィザードを開くには、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]プロジェクトのキューブデザイナーを開き、[**集計**] タブをクリックします。ツールバーの [**使用法に基づく最適化**] ボタンをクリックします。  
  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]内から使用法に基づく最適化ウィザードを開くには、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに接続し、 **[キューブ]** フォルダーを開きます。 キューブを選択して **[メジャー グループ]** フォルダーを開き、変更するメジャー グループを展開します。 **[パーティション]** フォルダーを右クリックし、 **[使用法に基づく最適化]** をクリックします。  
  
 こうした集計のデザインは、集計のデザイン ウィザードを使用して行います。 このウィザードでは、次の手順に従います。  
  
-   パーティション、メジャー グループ、またはキューブのストレージとキャッシュのオプションに対して、標準またはカスタムの設定を選択します。  
  
-   パーティション、メジャー グループ、またはキューブによって参照されるオブジェクトの推定カウントまたは実際のカウントを指定します。  
  
-   集計オプションと制限を指定して、デザインされた集計によって配信されるストレージとクエリのパフォーマンスを最適化します。  
  
-   パーティション、メジャー グループ、またはキューブの保存と処理 (省略可) を行い、定義された集計を生成します。  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の集計のデザイン ウィザードでは、集計デザインを提供するパーティション構造の統計分析に基づいて集計をデザインします。集計をデザインする際には、ストレージ サイズまたはパフォーマンスの推定向上度を制限できます。 集計のデザイン ウィザードを使用するとパーティションの全体的なパフォーマンスを向上させることができますが、このウィザードの集計デザインはビジネス ユーザーの特定のニーズに合致したものではありません。 使用法に基づく最適化ウィザードでは、こうした特定のニーズに合致した集計デザインが可能ですが、このためには [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスのクエリ ログに、こうしたクエリを構築するための十分な情報が記録されている必要があります。  
  
 通常、両方のウィザードを併用することで、配置後のパフォーマンスと長期的なパフォーマンスを向上させます。 パーティション (または、パーティションを含むキューブやメジャー グループ) を最初に配置するときに、まず集計のデザイン ウィザードを使用して全体的なパフォーマンスを向上させる必要があります。 その後、一定期間が経過してパーティションに対するビジネス ユーザーのクエリがクエリ ログに記録されたら、使用法に基づく最適化ウィザードを使用します。これにより、ビジネス ユーザーのクエリ要件に適応した、よりパフォーマンスの高い集計デザインを作成することができます。  
  
> [!NOTE]  
>  クエリ ログの構成については、「 [Analysis Services クエリ ログの構成](instances/log-operations-in-analysis-services.md?view=sql-server-2014#bkmk_querylog)」をご覧ください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [使用法に基づく最適化ウィザード &#40;変更するパーティションの選択&#41;](select-partitions-to-modify-usage-based-optimization-wizard.md)  
  
-   [使用法に基づく最適化ウィザードを &#40;クエリ条件を指定し&#41;](specify-query-criteria-usage-based-optimization-wizard.md)  
  
-   [使用法に基づく最適化ウィザード &#40;最適化されるクエリを確認し&#41;](review-the-queries-that-will-be-optimized-usage-based-optimization-wizard.md)  
  
-   [使用法に基づく最適化ウィザードを &#40;集計使用率を確認する&#41;](review-aggregation-usage-usage-based-optimiation-wizard.md)  
  
-   [&#40;使用法に基づく最適化ウィザードを使用してオブジェクト数を指定&#41;](specify-object-counts-usage-based-optimization-wizard.md)  
  
-   [集計オプションの設定 &#40;使用法に基づく最適化ウィザード&#41;](set-aggregation-options-usage-based-optimization-wizard.md)  
  
-   [ウィザードの完了 &#40;使用法に基づく最適化ウィザード&#41;](completing-the-wizard-usage-based-optimization-wizard.md)  
  
## <a name="see-also"></a>参照  
 [集計と集計のデザイン](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)   
 [多次元モデルのキューブ](multidimensional-models/cubes-in-multidimensional-models.md)   
 [集計のデザインウィザードの F1 ヘルプ](aggregation-design-wizard-f1-help.md)   
 [Analysis Services のウィザード &#40;多次元データ&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
