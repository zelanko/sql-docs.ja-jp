---
title: "計算 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- calculations [Analysis Services]
- OLAP objects [Analysis Services], calculations
- MDX [Analysis Services], calculations
- calculations [Analysis Services], about calculations
- cubes [Analysis Services], calculations
ms.assetid: 6be84916-fd05-4efc-ab98-6adbbad80154
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0771e03eaa12e37cce685309fa776fe7f7c31443
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="calculations"></a>計算
  計算は、多次元式 (MDX) 式またはキューブ内で計算されるメンバー、名前付きセット、またはスコープ割り当てを定義するために使用するスクリプト[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。 計算により、キューブのデータによって定義されるオブジェクトではなく、キューブの他の部分、他のキューブ、さらには [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの外部にある情報を参照できる式によって定義されるオブジェクトを追加できます。 計算により、キューブの機能を拡張し、ビジネス インテリジェンス アプリケーションの柔軟性と能力を向上させることができます。 計算スクリプトの作成の詳細については、次を参照してください。 [Microsoft SQL Server 2005 の MDX スクリプトの紹介](http://go.microsoft.com/fwlink/?LinkId=81892)です。 MDX クエリおよび計算に関連するパフォーマンスの問題の詳細については、次を参照してください。、 [SQL Server 2005 Analysis Services パフォーマンス ガイド](http://go.microsoft.com/fwlink/?LinkId=81621)です。  
  
## <a name="calculated-members"></a>計算されるメンバー  
 計算されるメンバーとは、値が実行時に計算されるメンバーのことです。その計算には、計算されるメンバーの定義時に指定した多次元式 (MDX) が使用されます。 計算されるメンバーは、ビジネス インテリジェンス アプリケーションで他のメンバーと同様に使用できます。 キューブに保存されるのは定義のみであるため、計算されるメンバーによってキューブのサイズが大きくなることはありません。値はクエリへの応答時にメモリ内で計算されます。  
  
 計算されるメンバーは、メジャー ディメンションを含むすべてのディメンションで定義できます。 メジャー ディメンションに作成された計算されるメンバーは、計算されるメジャーと呼ばれます。  
  
 通常、計算されるメンバーはキューブの既存のデータに基づいていますが、データに算術演算子、数値、および関数を組み合わせて複雑な式を作成することもできます。 また、LookupCube などの MDX 関数を使用し、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースにある他のキューブのデータにアクセスすることも可能です。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には標準化された Visual Studio 関数ライブラリが含まれているため、ストアド プロシージャを使用して、現在の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース以外のソースからデータを取得することができます。 ストアド プロシージャの詳細については、次を参照してください。[ストアド プロシージャを定義する](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)です。  
  
 たとえば、船会社の経営陣が積載量に対するコストに基づいて、利益の上がる貨物の種類を特定する場合を考えてみます。 経営陣が使用する Shipments キューブには、ディメンションとして Cargo、Fleet、および Time が含まれ、メジャーとして Price_to_Ship、Cost_to_Ship、および Volume_in_Cubic_Meters が含まれています。ただし、収益性に関するメジャーは含まれていません。 この場合、計算されるメンバーを Profit_per_Cubic_Meter という名前のメジャーとしてキューブに作成できます。その値を計算するには、次のように、式の中で既存のメジャーを組み合わせます。  
  
```  
([Measures].[Price_to_Ship] - [Measures].[Cost_to_Ship]) /  
[Measures].[Volume_in_Cubic_Meters]  
```  
  
 計算されるメンバーを作成した後、Shipments キューブを参照すると、Profit_per_Cubic_Meter が他のメジャーと共に表示されます。  
  
 計算されるメンバーを作成するには、使用、**計算**キューブ デザイナーのタブです。 詳細については、次を参照してください[計算されるメンバーの作成。](../../analysis-services/multidimensional-models/create-calculated-members.md)  
  
## <a name="named-sets"></a>名前付きセット  
 名前付きセットとは、セットを返す CREATE SET MDX ステートメント式であり、 MDX 式は、キューブの定義の一部として保存[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。 名前付きセットは、多次元式 (MDX) クエリで再使用するために作成されます。 名前付きセットを使用すると、ビジネス ユーザーは、クエリを簡素化し、複雑で頻繁に使用されるセット式にセット式ではなくセット名を使用できます。 **関連トピック:** [名前付きセットの作成](../../analysis-services/multidimensional-models/create-named-sets.md)  
  
## <a name="script-commands"></a>スクリプト コマンド  
 スクリプト コマンドは、キューブの定義の一部として含まれる MDX スクリプトです。 スクリプト コマンドを使用すると、キューブの一部のみに対する計算のスコープ割り当てなど、MDX でサポートされるほとんどすべてのアクションをキューブで実行できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、キューブ全体または特定のセクションでは、スクリプトの実行中の特定の時点で、キューブの MDX スクリプトを適用できます。 既定のスクリプト コマンドである CALCULATE ステートメントを実行すると、既定の範囲に基づいて、キューブのセルに集計データが設定されます。  
  
 既定の範囲はキューブ全体ですが、サブキューブと呼ばれる制限された範囲を定義して、特定のキューブ領域にのみ MDX スクリプトを適用することもできます。 SCOPE ステートメントは、範囲が終了するか、再定義されるまで、計算スクリプト内の後続の MDX 式およびステートメントのすべての範囲を定義します。 THIS ステートメントを使用すると、MDX 式を現在の範囲に適用できます。 BACK_COLOR ステートメントを使用すると、現在の範囲内のセルの背景色を指定して、デバッグに役立てることができます。  
  
 たとえば、スクリプト コマンドを使用すると、以前の期間の売上の重み付け値を基にして、期間と販売区域全体を対象に、販売ノルマを従業員に割り当てることができます。  
  
## <a name="see-also"></a>参照  
 [多次元モデルの計算](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)  
  
  
