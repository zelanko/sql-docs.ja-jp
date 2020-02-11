---
title: ディメンションの概要 (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], about dimensions
- storage [Analysis Services], dimensions
- dimensions [Analysis Services], examples
- storing data [Analysis Services], dimensions
- storage [Analysis Services]
ms.assetid: ab170fdd-4144-42db-9497-690b9189fc25
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2dce25d6638c5ec921ec22601ed73d03a2ccb215
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68887870"
---
# <a name="introduction-to-dimensions-analysis-services---multidimensional-data"></a>ディメンションの概要 (Analysis Services - 多次元データ)
  すべての[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Microsoft ディメンションは、データソースビュー内のテーブルまたはビューの列に基づいた属性のグループです。 ディメンションには、キューブとは無関係に存在するもの、複数のキューブ内で使用できるもの、および 1 つのキューブ内で複数回使用できるものがあり、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンス間でリンクできます。 キューブとは無関係に存在するディメンションをデータベース ディメンションといい、キューブ内のデータベース ディメンションとデータベース ディメンションのインスタンスをキューブ ディメンションといいます。  
  
## <a name="dimension-based-on-a-star-schema-design"></a>スター スキーマ デザインに基づくディメンション  
 ディメンションの構造は、主に、基になるディメンション テーブルの構造によって決まります。 最も単純な構造をスター スキーマといいます。このスキーマでは、各ディメンションが、主キーと外部キーのリレーションシップによってファクト テーブルに直接リンクされている 1 つのディメンション テーブルに基づいています。  
  
 次の[!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)]図は、サンプルデータベースのサブセクションを示しています。このサブセクションでは、 **FactResellerSales**ファクトテーブルが**DimReseller**と**DimPromotion**の2つのディメンションテーブルに関連付けられています。 **FactResellerSales**ファクトテーブルの**ResellerKey**列は、 **DimReseller**ディメンションテーブルの**ResellerKey**主キー列に対する外部キーリレーションシップを定義します。 同様に、 **FactResellerSales**ファクトテーブルの**PromotionKey**列は、 **DimPromotion**ディメンションテーブルの**PromotionKey**主キー列に対する外部キーリレーションシップを定義します。  
  
 ![ファクト ディメンションのリレーションシップの論理スキーマ](https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/dimfactrelationship.gif "ファクト ディメンションのリレーションシップの論理スキーマ")  
  
## <a name="dimension-based-on-a-snowflake-schema-design"></a>スノーフレーク スキーマ デザインに基づくディメンション  
 ディメンションを定義するには複数のテーブルからの情報を必要とするため、より複雑な構造が必要になることがよくあります。 この構造は、スノーフレーク スキーマといいます。このスキーマでは、各ディメンションが、最終的には主キーと外部キーのリレーションシップによってファクト テーブルにリンクされる、相互にリンクされた複数のテーブルの列の属性に基づいています。 たとえば、次の図は、 **AdventureWorksDW**サンプルプロジェクトの Product ディメンションを完全に記述するために必要なテーブルを示しています。  
  
 ![AdventureWorksAS の Product ディメンション用のテーブル](https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/dimproduct.gif "AdventureWorksAS の Product ディメンション用のテーブル")  
  
 製品を完全に記述するには、製品のカテゴリとサブカテゴリを Product ディメンションに含める必要があります。 ただし、この情報は、 **DimProduct**ディメンションのメインテーブルに直接は存在しません。 **DimProduct**から**DimProductSubcategory**への外部キーリレーションシップにより、 **DimProductCategory**テーブルとの外部キーリレーションシップがあるため、product ディメンションの製品カテゴリとサブカテゴリの情報を含めることができます。  
  
## <a name="snowflake-schema-versus-reference-relationship"></a>スノーフレーク スキーマと参照リレーションシップの対比  
 状況によっては、スノーフレーク スキーマを使用して 1 つのディメンション内の属性を複数のテーブルから定義するか、2 つの異なるディメンションを定義して、そのディメンション間の参照ディメンション リレーションシップを定義するか、選択が必要になる場合があります。 次の図は、このようなシナリオを示しています。  
  
 ![サンプルの参照されるディメンションの論理スキーマ](https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/dimindirect.gif "サンプルの参照されるディメンションの論理スキーマ")  
  
 上の図では、 **FactResellerSales**ファクトテーブルに、 **DimGeography**ディメンションテーブルとの外部キーリレーションシップがありません。 ただし、 **FactResellerSales**ファクトテーブルには、 **DimReseller**ディメンションテーブルとの外部キーリレーションシップがあります。このリレーションシップには、 **DimGeography**ディメンションテーブルとの外部キーリレーションシップがあります。 各リセラーに関する地理情報を含むリセラーディメンションを定義するには、 **DimGeography**ディメンションテーブルと**DimReseller**ディメンションテーブルからこれらの属性を取得する必要があります。 ただし [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で、2 つの異なるディメンションを作成し、その 2 つのディメンション間で参照ディメンション リレーションシップを定義することによりメジャー グループ内でこれらのディメンションをリンクしても、同じ結果を得られます。 参照ディメンションリレーションシップの詳細については、「[ディメンションリレーションシップ](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)」を参照してください。  
  
 このシナリオで参照ディメンション リレーションシップを使用することの利点の 1 つとして、1 つの地理ディメンションを作成した後、追加のストレージ領域を必要とすることなく、この地理ディメンションに基づいて、複数のキューブ ディメンションを作成できることが挙げられます。 たとえば、地理キューブ ディメンションの 1 つを販売店ディメンションにリンクし、別の地理キューブ ディメンションを顧客ディメンションにリンクすることができます。 **関連トピック:**[ディメンションリレーションシップ](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)、[参照リレーションシップと参照関係プロパティの定義](../multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)  
  
## <a name="processing-a-dimension"></a>ディメンションの処理  
 ディメンションを作成した後、ディメンション内の属性および階層のメンバーを表示するには、あらかじめこのディメンションを処理しておく必要があります。 ディメンションの構造が変更されたり、その基になるテーブルの情報が更新された場合、ディメンションをもう一度処理しないと、変更内容を表示できません。 構造の変更後にディメンションを処理する際は、そのディメンションが含まれたキューブも処理する必要があります。これを行わないと、キューブを表示できません。  
  
## <a name="security"></a>Security  
 ディメンションの従属オブジェクトは、階層、レベル、メンバーを含め、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のロールを使用してすべてセキュリティで保護されています。 ディメンションのセキュリティは、そのディメンションを使用するデータベース内のすべてのキューブ、または特定のキューブにのみ適用できます。 ディメンションセキュリティの詳細については、「[ディメンションに対する権限の許可 &#40;Analysis Services&#41;](../multidimensional-models/grant-permissions-on-a-dimension-analysis-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ディメンションストレージ](../multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md)   
 [ディメンションの翻訳](../multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)   
 [書き込み許可ディメンション](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
