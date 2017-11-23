---
title: "スキーマ生成ウィザード (Analysis Services) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: relational schema [Analysis Services]
ms.assetid: 68bf7ba3-d0cb-437f-9a3e-9edc0999af19
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f4c43ae5e0b38aab494f21237986b958286d7b9b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="schema-generation-wizard-analysis-services"></a>スキーマ生成ウィザード (Analysis Services)
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトまたはデータベース内で OLAP プロジェクトを定義する際の、2 種類のリレーショナル スキーマ操作方法をサポートしています。 一般的に、OLAP オブジェクトは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトまたはデータベース内のデータ ソース ビューで作成される論理データ モデルに基づいて定義します。 このデータ ソース ビューは、データ ソース ビューでカスタマイズされる、1 つ以上のリレーショナル データ ソースのスキーマ要素に基づいて定義されます。  
  
 または、OLAP オブジェクトを最初に定義してから、これらの OLAP オブジェクトをサポートするデータ ソース ビュー、データ ソース、および基になるリレーショナル データベース スキーマを生成することもできます。 このリレーショナル データベースは、サブジェクト領域データベースと呼ばれます。  
  
 この方法はトップダウン デザインと呼ばれることもあり、プロトタイプや分析モデルの作成によく使用されます。 このアプローチに従う場合は、スキーマ生成ウィザードを使用することによって、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のプロジェクトまたはデータベースで定義されている OLAP オブジェクトに基づいて、基になるデータ ソース ビューとデータ ソース オブジェクトを作成します。  
  
 これは、反復的なアプローチです。 ほとんどの場合、ディメンションとキューブのデザインを変更するためにウィザードを何度か再実行することになります。 ウィザードを実行するたびに、基になるオブジェクトに変更内容が組み込まれ、基になるデータベースに含まれているデータができる限り保持されます。  
  
 生成されるスキーマは、SQL Server のリレーショナル データベース エンジン スキーマです。 このウィザードでは、他のリレーショナル データベース製品のスキーマは生成されません。  
  
 サブジェクト領域データベースに入力されるデータは、SQL Server のリレーショナル データベースに入力するときに使用するツールとテクニックを使用して、別々に追加されます。 ほとんどの場合、データはウィザードを再実行したときに保持されますが、例外もあります。 たとえば、データを含んでいるディメンションまたは属性を削除した場合は、一部のデータが失われます。 スキーマが変更されたため、スキーマ生成ウィザードで一部のデータを削除する必要がある場合は、データが削除される前に警告が表示されるので、再生成をキャンセルできます。  
  
 一般的に、スキーマ生成ウィザードによって生成されたオブジェクトに対する変更は、スキーマ生成ウィザードが次にそのオブジェクトを再生成したときに上書きされます。 この主な例外は、スキーマ生成ウィザードで生成されたテーブルに列を追加する場合です。 この場合、スキーマ生成ウィザードによって、テーブルに追加した列だけでなく、その列のデータも保持されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 次の表に、スキーマ生成ウィザードの操作方法を説明するその他のトピックを示します。  
  
|トピック|Description|  
|-----------|-----------------|  
|[スキーマ生成ウィザードの使用 (Analysis Services)](../../analysis-services/multidimensional-models/use-the-schema-generation-wizard-analysis-services.md)|サブジェクト領域データベースとステージング領域データベースのスキーマの生成方法について説明します。|  
|[データベース スキーマの理解](../../analysis-services/multidimensional-models/understanding-the-database-schemas.md)|サブジェクト領域データベースとステージング領域データベースに対して生成されるスキーマについて説明します。|  
|[増分生成の理解](../../analysis-services/multidimensional-models/understanding-incremental-generation.md)|スキーマ生成ウィザードの増分生成機能について説明します。|  
  
## <a name="see-also"></a>参照  
 [多次元モデルのデータ ソース ビュー](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [多次元モデルのデータ ソース](../../analysis-services/multidimensional-models/data-sources-in-multidimensional-models.md)   
 [サポートされるデータ ソース &#40;SSASSSAS - 多次元&#41;](../../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
  
