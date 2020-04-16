---
title: ディメンションの概要 (分析サービス - 多次元データ) |マイクロソフトドキュメント
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
ms.openlocfilehash: e1a78735cd5aee5ebc87adaac6fab48bb4e183d6
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "81387902"
---
# <a name="introduction-to-dimensions-analysis-services---multidimensional-data"></a>ディメンションの概要 (Analysis Services - 多次元データ)
  Microsoft[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のディメンションはすべて、データ ソース ビューのテーブルまたはビューの列に基づく属性のグループです。 ディメンションには、キューブとは無関係に存在するもの、複数のキューブ内で使用できるもの、および 1 つのキューブ内で複数回使用できるものがあり、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンス間でリンクできます。 キューブとは無関係に存在するディメンションをデータベース ディメンションといい、キューブ内のデータベース ディメンションとデータベース ディメンションのインスタンスをキューブ ディメンションといいます。  
  
## <a name="dimension-based-on-a-star-schema-design"></a>スター スキーマ デザインに基づくディメンション  
 ディメンションの構造は、主に、基になるディメンション テーブルの構造によって決まります。 最も単純な構造をスター スキーマといいます。このスキーマでは、各ディメンションが、主キーと外部キーのリレーションシップによってファクト テーブルに直接リンクされている 1 つのディメンション テーブルに基づいています。  
  
 次の図は、[!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)]**サンプル**データベースのサブセクションを示しています。 **DimReseller** **DimPromotion** **ファクトリセラーの売上**ファクト テーブルの **[リ**セラー キー] 列は **、DimReseller**ディメンション テーブルの **[リセラーキー主キー** ] 列との外部キー リレーションシップを定義します。 同様に、**ファクトリセラーの売上**ファクト テーブルの**プロモーションキー**列は **、DimPromotion**ディメンション テーブルの**プロモーションキー**主キー列に対する外部キー リレーションシップを定義します。  
  
 ![ファクト ディメンションのリレーションシップの論理スキーマ](../../analysis-services/dev-guide/media/dimfactrelationship.gif "ファクト ディメンションのリレーションシップの論理スキーマ")  
  
## <a name="dimension-based-on-a-snowflake-schema-design"></a>スノーフレーク スキーマ デザインに基づくディメンション  
 ディメンションを定義するには複数のテーブルからの情報を必要とするため、より複雑な構造が必要になることがよくあります。 この構造は、スノーフレーク スキーマといいます。このスキーマでは、各ディメンションが、最終的には主キーと外部キーのリレーションシップによってファクト テーブルにリンクされる、相互にリンクされた複数のテーブルの列の属性に基づいています。 たとえば、次の図は **、AdventureWorksDW**サンプル プロジェクトの製品ディメンションを完全に記述するために必要なテーブルを示しています。  
  
 ![AdventureWorksAS の Product ディメンション用のテーブル](../../analysis-services/dev-guide/media/dimproduct.gif "AdventureWorksAS の Product ディメンション用のテーブル")  
  
 製品を完全に記述するには、製品のカテゴリとサブカテゴリを Product ディメンションに含める必要があります。 ただし、その情報は**DimProduct**ディメンションのメイン テーブルに直接格納されません。 **DimProduct**から**DimProductSubcategory**への外部キー リレーションシップは **、DimProductCategory**テーブルとの外部キー リレーションシップを持つため、製品カテゴリとサブカテゴリの情報を製品ディメンションに含めることができます。  
  
## <a name="snowflake-schema-versus-reference-relationship"></a>スノーフレーク スキーマと参照リレーションシップの対比  
 状況によっては、スノーフレーク スキーマを使用して 1 つのディメンション内の属性を複数のテーブルから定義するか、2 つの異なるディメンションを定義して、そのディメンション間の参照ディメンション リレーションシップを定義するか、選択が必要になる場合があります。 次の図は、このようなシナリオを示しています。  
  
 ![サンプルの参照されるディメンションの論理スキーマ](../../analysis-services/dev-guide/media/dimindirect.gif "サンプルの参照されるディメンションの論理スキーマ")  
  
 前の図では、**ファクトリセラーの売上**ファクト テーブルには **、DimGeography**ディメンション テーブルとの外部キー リレーションシップがありません。 ただし **、FactResellerSales**ファクト テーブルには **、DimReseller**ディメンション テーブルとの外部キー リレーションシップがあり、そのテーブルは**DimGeography**ディメンション テーブルと外部キー リレーションシップを持ちます。 各リセラーに関する地理情報を含むリセラー ディメンションを定義するには、これらの属性を**DimGeography**および**DimReseller**ディメンション テーブルから取得する必要があります。 ただし [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で、2 つの異なるディメンションを作成し、その 2 つのディメンション間で参照ディメンション リレーションシップを定義することによりメジャー グループ内でこれらのディメンションをリンクしても、同じ結果を得られます。 参照ディメンションのリレーションシップの詳細については、「[ディメンション リレーションシップ](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)」を参照してください。  
  
 このシナリオで参照ディメンション リレーションシップを使用することの利点の 1 つとして、1 つの地理ディメンションを作成した後、追加のストレージ領域を必要とすることなく、この地理ディメンションに基づいて、複数のキューブ ディメンションを作成できることが挙げられます。 たとえば、地理キューブ ディメンションの 1 つを販売店ディメンションにリンクし、別の地理キューブ ディメンションを顧客ディメンションにリンクすることができます。 **関連項目:**[ディメンション リレーションシップ](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)、[参照されるリレーションシップおよび参照されるリレーションシッププロパティの定義](../multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)  
  
## <a name="processing-a-dimension"></a>ディメンションの処理  
 ディメンションを作成した後、ディメンション内の属性および階層のメンバーを表示するには、あらかじめこのディメンションを処理しておく必要があります。 ディメンションの構造が変更されたり、その基になるテーブルの情報が更新された場合、ディメンションをもう一度処理しないと、変更内容を表示できません。 構造の変更後にディメンションを処理する際は、そのディメンションが含まれたキューブも処理する必要があります。これを行わないと、キューブを表示できません。  
  
## <a name="security"></a>セキュリティ  
 ディメンションの従属オブジェクトは、階層、レベル、メンバーを含め、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のロールを使用してすべてセキュリティで保護されています。 ディメンションのセキュリティは、そのディメンションを使用するデータベース内のすべてのキューブ、または特定のキューブにのみ適用できます。 ディメンション セキュリティの詳細については、「[分析サービス&#41;&#40;ディメンションに対するアクセス許可を付与](../multidimensional-models/grant-permissions-on-a-dimension-analysis-services.md)する 」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ディメンションの格納](../multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md)   
 [ディメンションの翻訳](../multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)   
 [書き込み許可ディメンション](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
