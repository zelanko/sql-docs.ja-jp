---
title: 論理アーキテクチャ (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- logical architecture [Analysis Services Multidimensional Data]
ms.assetid: 1b9cae0a-8990-4194-af5f-a1ea5f2aff06
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 074659d42e1960c5f24cf4afa20668a3d8c823b0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62725486"
---
# <a name="logical-architecture-analysis-services---multidimensional-data"></a>論理アーキテクチャ (Analysis Services - 多次元データ)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]では、サーバーコンポーネントとクライアントコンポーネントの両方を使用して、ビジネスインテリジェンスアプリケーションのオンライン分析処理 (OLAP) およびデータマイニング機能を提供し[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]ます。  
  
-   [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のサーバー コンポーネントは、Microsoft Windows サービスとして実装されます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]は、同じコンピューター上の複数のインスタンスをサポートし[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 、の各インスタンスは Windows サービスの個別のインスタンスとして実装されます。  
  
-   クライアントは、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] との通信に、コマンドの発行や応答の受信のための SOAP ベースのプロトコルで、Web サービスとして公開されているパブリック標準の XML for Analysis (XMLA) を使用します。 クライアント オブジェクト モデルも XMLA 経由で提供されます。クライアント オブジェクト モデルには、ADOMD.NET などのマネージド プロバイダーまたはネイティブ OLE DB プロバイダーを使用してアクセスできます。  
  
-   クエリ コマンドは、SQL、分析用の業界標準クエリ言語である多次元式 (MDX)、またはデータ マイニング指向の業界標準クエリ言語であるデータ マイニング拡張機能 (DMX) を使用して発行できます。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベース オブジェクトの管理には、Analysis Services スクリプト言語 (ASSL) を使用することもできます。  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、接続されていないクライアント上のアプリケーションがローカルに格納された多次元データを参照することを可能にするローカル キューブ エンジンもサポートされます。 詳細については、「 [Analysis Services の開発に関するクライアントアーキテクチャの要件](../olap-physical/client-architecture-requirements-for-analysis-services-development.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 **論理アーキテクチャの概要**  
 [論理アーキテクチャの概要 &#40;Analysis Services-多次元データ&#41;](logical-architecture-overview-analysis-services-multidimensional-data.md)  
  
 **Server オブジェクト**  
 [サーバーオブジェクト &#40;Analysis Services-多次元データ&#41;](server-objects-analysis-services-multidimensional-data.md)  
  
 **データベースオブジェクト**  
 [データベース オブジェクト &#40;Analysis Services - 多次元データ&#41;](database-objects-analysis-services-multidimensional-data.md)  
  
 **Dimension オブジェクト**  
 [ディメンションオブジェクト &#40;Analysis Services-多次元データ&#41;](../../multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 **[キューブ オブジェクト]**  
 [キューブオブジェクト &#40;Analysis Services-多次元データ&#41;](../../multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 **ユーザー アクセス セキュリティ**  
 [ユーザー アクセス セキュリティ アーキテクチャ](understanding-microsoft-olap-logical-architecture.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft OLAP アーキテクチャについて](../olap-physical/understanding-microsoft-olap-architecture.md)   
 [物理アーキテクチャ &#40;Analysis Services - 多次元データ&#41;](../olap-physical/understanding-microsoft-olap-physical-architecture.md)  
  
  
