---
title: Dimension オブジェクト (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], objects
ms.assetid: 7f3d55c7-cccb-4ad0-b6cb-3a2c9992dd68
author: minewiskan
ms.author: owend
ms.openlocfilehash: 02bb6a26b04a2fb79994e192c9c62a7cb362476c
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545162"
---
# <a name="dimension-objects-analysis-services---multidimensional-data"></a>Dimension オブジェクト (Analysis Services - 多次元データ)
  簡単な <xref:Microsoft.AnalysisServices.Dimension> オブジェクトは、基本情報、属性、および階層で構成されます。 基本情報には、ディメンションの名前、ディメンションの種類、データ ソース、ストレージ モードなどが含まれます。 属性は、ディメンション内の実際のデータを定義します。 属性は必ずしも階層に属するわけではありませんが、階層は属性から構築されます。 階層は、順序付けされたレベルの一覧を作成し、ユーザーに可能なディメンションの探索方法を定義します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 次のトピックでは、ディメンション オブジェクトの設計方法と実装方法の詳細について説明します。  
  
|トピック|説明|  
|-----------|-----------------|  
|[ディメンション &#40;Analysis Services - 多次元データ&#41;](dimensions-analysis-services-multidimensional-data.md)|で [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、ディメンションはキューブの基本コンポーネントです。 ディメンションは、顧客、店舗、従業員など、ユーザーが関心のある分野に関するデータを編成します。|  
|[属性と属性階層](attributes-and-attribute-hierarchies.md)|ディメンションとは属性のコレクションで、これらの属性はデータ ソース ビュー内のテーブルまたはビューの 1 つ以上の列にバインドされています。|  
|[のディメンション デザイナーでは、[ディメンション構造] ビューの](attribute-relationships.md)|では [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、ディメンション内の属性は常に、直接または間接的にキー属性に関連付けられます。 同一のリレーショナル テーブルからすべてのディメンション属性が派生するスター スキーマに基づいてディメンションを定義すると、ディメンションのキー属性と各非キー属性の間に自動的に属性リレーションシップが定義されます。 関連を持った複数のテーブルからディメンション属性が派生するスノーフレーク スキーマを基にディメンションを定義すると、属性リレーションシップが自動的に次のように定義されます。<br /><br /> -キー属性と、メインディメンションテーブルの列にバインドされている各非キー属性の間<br />-キー属性と、基になるディメンションテーブルをリンクするセカンダリテーブルの外部キーにバインドされた属性の間<br />-セカンダリテーブルの外部キーにバインドされた属性と、セカンダリテーブルの列にバインドされている各非キー属性の間。|  
  
  
