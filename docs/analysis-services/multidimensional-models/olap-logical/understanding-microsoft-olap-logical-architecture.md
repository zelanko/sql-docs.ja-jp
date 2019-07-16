---
title: 論理アーキテクチャ (Analysis Services - 多次元データ) |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6b6b33ffbf59cf05bc5455d3daac437e9e79407c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68165599"
---
# <a name="understanding-microsoft-olap-logical-architecture"></a>Microsoft OLAP 論理アーキテクチャについて
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーとクライアントの両方のコンポーネントを使用して、オンライン分析処理 (OLAP) およびビジネス インテリジェンス アプリケーション用のデータ マイニング機能を提供します。  
  
-   [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のサーバー コンポーネントは、Microsoft Windows サービスとして実装されます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 各インスタンスで、同じコンピューターに複数のインスタンスをサポートしている[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]Windows サービスの個別のインスタンスとして実装されています。  
  
-   クライアントは、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] との通信に、コマンドの発行や応答の受信のための SOAP ベースのプロトコルで、Web サービスとして公開されているパブリック標準の XML for Analysis (XMLA) を使用します。 クライアント オブジェクト モデルも XMLA 経由で提供されます。クライアント オブジェクト モデルには、ADOMD.NET などのマネージド プロバイダーまたはネイティブ OLE DB プロバイダーを使用してアクセスできます。  
  
-   次の言語を使用して、クエリ コマンドを発行できます。SQL;多次元式 (MDX)、分析用の業界標準クエリ言語またはデータ マイニング拡張機能 (DMX)、データ マイニング指向、業界標準クエリ言語を選択します。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベース オブジェクトの管理には、Analysis Services スクリプト言語 (ASSL) を使用することもできます。  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、接続されていないクライアント上のアプリケーションがローカルに格納された多次元データを参照することを可能にするローカル キューブ エンジンもサポートされます。 詳細については、次を参照してください[Analysis Services 開発に関するクライアント アーキテクチャの要件。](../../../analysis-services/multidimensional-models/olap-physical/client-architecture-requirements-for-analysis-services-development.md)  
  
## <a name="in-this-section"></a>このセクションの内容  
 **論理アーキテクチャの概要**  
 [論理アーキテクチャの概要&#40;Analysis Services - 多次元データ&#41;](../../../analysis-services/multidimensional-models/olap-logical/logical-architecture-overview-analysis-services-multidimensional-data.md)  
  
 **サーバー オブジェクト**  
 [サーバー オブジェクト&#40;Analysis Services - 多次元データ&#41;](../../../analysis-services/multidimensional-models/olap-logical/server-objects-analysis-services-multidimensional-data.md)  
  
 **データベース オブジェクト**  
 [データベース オブジェクト &#40;Analysis Services - 多次元データ&#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
 **ディメンション オブジェクト**  
 [ディメンション オブジェクト&#40;Analysis Services - 多次元データ&#41;](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 **キューブ オブジェクト**  
 [キューブ オブジェクト&#40;Analysis Services - 多次元データ&#41;](../../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 **ユーザー アクセス セキュリティ**  
 [ユーザー アクセスのセキュリティ アーキテクチャ](http://msdn.microsoft.com/library/71b44e10-2bd0-44f7-8de9-7c8f5b7ac082)  
  
## <a name="see-also"></a>関連項目  
 [Microsoft OLAP アーキテクチャをについてください。](../../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)   
 [物理アーキテクチャ&#40;Analysis Services - 多次元データ&#41;](../../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-physical-architecture.md)  
  
  
