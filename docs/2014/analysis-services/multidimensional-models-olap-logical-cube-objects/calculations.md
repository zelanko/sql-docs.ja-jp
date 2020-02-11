---
title: 計算 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- calculations [Analysis Services]
- OLAP objects [Analysis Services], calculations
- MDX [Analysis Services], calculations
- calculations [Analysis Services], about calculations
- cubes [Analysis Services], calculations
ms.assetid: 6be84916-fd05-4efc-ab98-6adbbad80154
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 871d248eec557033c181bbd3d162cd17875dd30c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62702693"
---
# <a name="calculations"></a>[新しい名前付きセット]
  計算は、の[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]キューブで計算されるメンバー、名前付きセット、またはスコープ割り当てを定義するために使用される多次元式 (MDX) 式またはスクリプトです。 計算により、キューブのデータによって定義されるオブジェクトではなく、キューブの他の部分、他のキューブ、さらには [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの外部にある情報を参照できる式によって定義されるオブジェクトを追加できます。 計算により、キューブの機能を拡張し、ビジネス インテリジェンス アプリケーションの柔軟性と能力を向上させることができます。 スクリプト計算の詳細については、「 [Microsoft SQL Server 2005 での MDX スクリプトの概要](https://go.microsoft.com/fwlink/?LinkId=81892)」を参照してください。 MDX クエリおよび計算に関連するパフォーマンスの問題の詳細については、「 [SQL Server 2005 Analysis Services パフォーマンスガイド](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide)」を参照してください。  
  
## <a name="calculated-members"></a>計算されるメンバー  
 計算されるメンバーとは、値が実行時に計算されるメンバーのことです。その計算には、計算されるメンバーの定義時に指定した多次元式 (MDX) が使用されます。 計算されるメンバーは、ビジネス インテリジェンス アプリケーションで他のメンバーと同様に使用できます。 キューブに保存されるのは定義のみであるため、計算されるメンバーによってキューブのサイズが大きくなることはありません。値はクエリへの応答時にメモリ内で計算されます。  
  
 計算されるメンバーは、メジャー ディメンションを含むすべてのディメンションで定義できます。 メジャー ディメンションに作成された計算されるメンバーは、計算されるメジャーと呼ばれます。  
  
 通常、計算されるメンバーはキューブの既存のデータに基づいていますが、データに算術演算子、数値、および関数を組み合わせて複雑な式を作成することもできます。 また、LookupCube などの MDX 関数を使用し、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースにある他のキューブのデータにアクセスすることも可能です。 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には標準化された Visual Studio 関数ライブラリが含まれているため、ストアド プロシージャを使用して、現在の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース以外のソースからデータを取得することができます。 ストアドプロシージャの詳細については、「[ストアドプロシージャの定義](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)」を参照してください。  
  
 たとえば、船会社の経営陣が積載量に対するコストに基づいて、利益の上がる貨物の種類を特定する場合を考えてみます。 経営陣が使用する Shipments キューブには、ディメンションとして Cargo、Fleet、および Time が含まれ、メジャーとして Price_to_Ship、Cost_to_Ship、および Volume_in_Cubic_Meters が含まれています。ただし、収益性に関するメジャーは含まれていません。 この場合、計算されるメンバーを Profit_per_Cubic_Meter という名前のメジャーとしてキューブに作成できます。その値を計算するには、次のように、式の中で既存のメジャーを組み合わせます。  
  
```  
([Measures].[Price_to_Ship] - [Measures].[Cost_to_Ship]) /  
[Measures].[Volume_in_Cubic_Meters]  
```  
  
 計算されるメンバーを作成した後、Shipments キューブを参照すると、Profit_per_Cubic_Meter が他のメジャーと共に表示されます。  
  
 計算されるメンバーを作成するには、キューブデザイナーの [**計算**] タブを使用します。 詳細については、「[計算されるメンバーの作成](../multidimensional-models/create-calculated-members.md)」を参照してください。  
  
## <a name="named-sets"></a>名前付きセット  
 名前付きセットとは、セットを返す CREATE SET MDX ステートメント式であり、 MDX 式は、のキューブ[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]の定義の一部として保存されます。 名前付きセットは、多次元式 (MDX) クエリで再使用するために作成されます。 名前付きセットを使用すると、ビジネス ユーザーは、クエリを簡素化し、複雑で頻繁に使用されるセット式にセット式ではなくセット名を使用できます。 **関連トピック:** [名前付きセットの作成](../multidimensional-models/create-named-sets.md)  
  
## <a name="script-commands"></a>スクリプト コマンド  
 スクリプト コマンドは、キューブの定義の一部として含まれる MDX スクリプトです。 スクリプト コマンドを使用すると、キューブの一部のみに対する計算のスコープ割り当てなど、MDX でサポートされるほとんどすべてのアクションをキューブで実行できます。 で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]は、MDX スクリプトをキューブ全体に適用することも、スクリプトの実行を通じて特定の時点でキューブの特定のセクションに適用することもできます。 既定のスクリプト コマンドである CALCULATE ステートメントを実行すると、既定の範囲に基づいて、キューブのセルに集計データが設定されます。  
  
 既定の範囲はキューブ全体ですが、サブキューブと呼ばれる制限された範囲を定義して、特定のキューブ領域にのみ MDX スクリプトを適用することもできます。 SCOPE ステートメントは、範囲が終了するか、再定義されるまで、計算スクリプト内の後続の MDX 式およびステートメントのすべての範囲を定義します。 THIS ステートメントを使用すると、MDX 式を現在の範囲に適用できます。 BACK_COLOR ステートメントを使用すると、現在の範囲内のセルの背景色を指定して、デバッグに役立てることができます。  
  
 たとえば、スクリプト コマンドを使用すると、以前の期間の売上の重み付け値を基にして、期間と販売区域全体を対象に、販売ノルマを従業員に割り当てることができます。  
  
## <a name="see-also"></a>参照  
 [多次元モデルの計算](../multidimensional-models/calculations-in-multidimensional-models.md)  
  
  
