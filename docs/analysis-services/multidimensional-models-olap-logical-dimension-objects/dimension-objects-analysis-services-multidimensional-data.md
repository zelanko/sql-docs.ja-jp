---
title: "ディメンション オブジェクト (Analysis Services - 多次元データ) |Microsoft ドキュメント"
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
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- dimensions [Analysis Services], objects
ms.assetid: 7f3d55c7-cccb-4ad0-b6cb-3a2c9992dd68
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 68fa5e37c0cc3620417f916ff35dcd6e3402d615
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="dimension-objects-analysis-services---multidimensional-data"></a>Dimension オブジェクト (Analysis Services - 多次元データ)
  簡単な <xref:Microsoft.AnalysisServices.Dimension> オブジェクトは、基本情報、属性、および階層で構成されます。 基本情報には、ディメンションの名前、ディメンションの種類、データ ソース、ストレージ モードなどが含まれます。 属性は、ディメンション内の実際のデータを定義します。 属性は必ずしも階層に属するわけではありませんが、階層は属性から構築されます。 階層は、順序付けされたレベルの一覧を作成し、ユーザーに可能なディメンションの探索方法を定義します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 次のトピックでは、ディメンション オブジェクトの設計方法と実装方法の詳細について説明します。  
  
|トピック|Description|  
|-----------|-----------------|  
|[ディメンション &#40;Analysis Services - 多次元データ&#41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ディメンションはキューブの基本的なコンポーネントです。 ディメンションは、顧客、店舗、従業員など、ユーザーが関心のある分野に関するデータを編成します。|  
|[属性と属性階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)|ディメンションとは属性のコレクションで、これらの属性はデータ ソース ビュー内のテーブルまたはビューの 1 つ以上の列にバインドされています。|  
|[のディメンション デザイナーの](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]属性、ディメンション内で常に関連している直接的または間接的にキー属性にします。 同一のリレーショナル テーブルからすべてのディメンション属性が派生するスター スキーマに基づいてディメンションを定義すると、ディメンションのキー属性と各非キー属性の間に自動的に属性リレーションシップが定義されます。 関連を持った複数のテーブルからディメンション属性が派生するスノーフレーク スキーマを基にディメンションを定義すると、属性リレーションシップが自動的に次のように定義されます。<br /><br /> キー属性と、メイン ディメンション テーブルの列にバインドされた各非キー属性の間<br /><br /> キー属性と、基になるディメンション テーブルにリンクしているセカンダリ テーブルの外部キーにバインドされた属性の間<br /><br /> セカンダリ テーブルの外部キーにバインドされた属性と、セカンダリ テーブルの列にバインドされた各非キー属性の間|  
  
  

