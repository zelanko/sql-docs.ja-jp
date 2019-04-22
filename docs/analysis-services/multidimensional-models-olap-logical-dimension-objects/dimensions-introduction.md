---
title: ディメンション (Analysis Services - 多次元データ) の概要 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b5f47146f02559e9b546d7e5ec164462ad2fdba1
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59042401"
---
# <a name="dimensions---introduction"></a>ディメンション - 概要
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  すべての Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ディメンションは、データ ソース ビューのテーブルまたはビューから列に基づいて属性のグループ。 ディメンション、キューブの独立して存在、複数のキューブで使用できる、1 つのキューブで複数回を使用できますおよび間でリンクできます[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンス。 キューブとは無関係に存在するディメンションをデータベース ディメンションといい、キューブ内のデータベース ディメンションとデータベース ディメンションのインスタンスをキューブ ディメンションといいます。  
  
## <a name="dimension-based-on-a-star-schema-design"></a>スター スキーマ デザインに基づくディメンション  
 ディメンションの構造は、主に、基になるディメンション テーブルの構造によって決まります。 最も単純な構造をスター スキーマといいます。このスキーマでは、各ディメンションが、主キーと外部キーのリレーションシップによってファクト テーブルに直接リンクされている 1 つのディメンション テーブルに基づいています。  
  
 次の図のサブセクションを示しています、[!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)]サンプル データベースでは、これで、 **FactResellerSales**ファクト テーブルが 2 つのディメンション テーブルに関連する**DimReseller**と**DimPromotion**します。 **ResellerKey**内の列、 **FactResellerSales**ファクト テーブルが外部キー リレーションシップを定義、 **ResellerKey**主キー列で、 **DimReseller**ディメンション テーブル。 同様に、 **PromotionKey**内の列、 **FactResellerSales**ファクト テーブルが外部キー リレーションシップを定義、 **PromotionKey** の主キー列**DimPromotion**ディメンション テーブル。  
  
 ![ファクト ディメンションのリレーションシップの論理スキーマ](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/media/dimfactrelationship.gif "ファクト ディメンションのリレーションシップの論理スキーマ")  
  
## <a name="dimension-based-on-a-snowflake-schema-design"></a>スノーフレーク スキーマ デザインに基づくディメンション  
 ディメンションを定義するには複数のテーブルからの情報を必要とするため、より複雑な構造が必要になることがよくあります。 この構造は、スノーフレーク スキーマといいます。このスキーマでは、各ディメンションが、最終的には主キーと外部キーのリレーションシップによってファクト テーブルにリンクされる、相互にリンクされた複数のテーブルの列の属性に基づいています。 たとえば、次の図はで、Product ディメンションを完全に記述するために必要なテーブルを示しています。、 **AdventureWorksDW**サンプル プロジェクト。  
  
 ![AdventureWorksAS の Product ディメンションのテーブル](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/media/dimproduct.gif "AdventureWorksAS の Product ディメンションのテーブル")  
  
 製品を完全に記述するには、製品のカテゴリとサブカテゴリを Product ディメンションに含める必要があります。 ただし、その情報がメイン テーブルに直接存在しない、 **DimProduct**ディメンション。 外部キー リレーションシップ**DimProduct**に**DimProductSubcategory**、外部キー リレーションシップがさらに、 **DimProductCategory**の表に、使用すると、Product ディメンションに製品カテゴリとサブカテゴリの情報を含める可能。  
  
## <a name="snowflake-schema-versus-reference-relationship"></a>スノーフレーク スキーマと参照リレーションシップの対比  
 状況によっては、スノーフレーク スキーマを使用して 1 つのディメンション内の属性を複数のテーブルから定義するか、2 つの異なるディメンションを定義して、そのディメンション間の参照ディメンション リレーションシップを定義するか、選択が必要になる場合があります。 次の図は、このようなシナリオを示しています。  
  
 ![サンプルの参照ディメンションの論理スキーマ](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/media/dimindirect.gif "サンプル参照ディメンションの論理スキーマ")  
  
 前の図で、 **FactResellerSales**ファクト テーブルに外部キー リレーションシップがない、 **DimGeography**ディメンション テーブル。 ただし、 **FactResellerSales**ファクト テーブルに外部キー リレーションシップが、 **DimReseller**さらにディメンション テーブルが外部キー リレーションシップ、 **DimGeography**ディメンション テーブル。 各販売店に関する地理情報を含む Reseller ディメンションを定義する必要がありますからこれらの属性を取得する、 **DimGeography**と**DimReseller**ディメンション テーブル。 ただし [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で、2 つの異なるディメンションを作成し、その 2 つのディメンション間で参照ディメンション リレーションシップを定義することによりメジャー グループ内でこれらのディメンションをリンクしても、同じ結果を得られます。 参照ディメンション リレーションシップの詳細については、次を参照してください。[ディメンション リレーションシップ](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)します。  
  
 このシナリオで参照ディメンション リレーションシップを使用することの利点の 1 つとして、1 つの地理ディメンションを作成した後、追加のストレージ領域を必要とすることなく、この地理ディメンションに基づいて、複数のキューブ ディメンションを作成できることが挙げられます。 たとえば、地理キューブ ディメンションの 1 つを販売店ディメンションにリンクし、別の地理キューブ ディメンションを顧客ディメンションにリンクすることができます。 **関連トピック:**[ディメンション リレーションシップ](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)、[参照リレーションシップと参照リレーションシップのプロパティを定義します。](../../analysis-services/multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)  
  
## <a name="processing-a-dimension"></a>ディメンションの処理  
 ディメンションを作成した後、ディメンション内の属性および階層のメンバーを表示するには、あらかじめこのディメンションを処理しておく必要があります。 ディメンションの構造が変更されたり、その基になるテーブルの情報が更新された場合、ディメンションをもう一度処理しないと、変更内容を表示できません。 構造の変更後にディメンションを処理する際は、そのディメンションが含まれたキューブも処理する必要があります。これを行わないと、キューブを表示できません。  
  
## <a name="security"></a>セキュリティ  
 ディメンションの従属オブジェクトは、階層、レベル、メンバーを含め、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のロールを使用してすべてセキュリティで保護されています。 ディメンションのセキュリティは、そのディメンションを使用するデータベース内のすべてのキューブ、または特定のキューブにのみ適用できます。 ディメンション セキュリティの詳細については、次を参照してください。[ディメンションに対する権限を付与&#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-permissions-on-a-dimension-analysis-services.md)します。  
  
## <a name="see-also"></a>参照  
 [ディメンションのストレージ](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md)   
 [ディメンションの翻訳](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)   
 [書き込み許可ディメンション](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
