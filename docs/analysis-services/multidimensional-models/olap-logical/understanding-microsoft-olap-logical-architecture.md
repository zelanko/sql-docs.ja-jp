---
title: "論理アーキテクチャ (Analysis Services - 多次元データ) |Microsoft ドキュメント"
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
- Analysis Services, architecture
- logical architecture [Analysis Services Multidimensional Data]
ms.assetid: 1b9cae0a-8990-4194-af5f-a1ea5f2aff06
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 454dddc6914853bf202376c47a1c929a0df4a6ac
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="understanding-microsoft-olap-logical-architecture"></a>Microsoft OLAP 論理アーキテクチャをについてください。
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]オンライン分析処理 (OLAP) とビジネス インテリジェンス アプリケーション用のデータ マイニング機能を指定するサーバーとクライアントの両方のコンポーネントを使用します。  
  
-   [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のサーバー コンポーネントは、Microsoft Windows サービスとして実装されます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]の各インスタンスと、同じコンピューターに複数のインスタンスをサポートしている[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]Windows サービスの個別のインスタンスとして実装します。  
  
-   クライアントは、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] との通信に、コマンドの発行や応答の受信のための SOAP ベースのプロトコルで、Web サービスとして公開されているパブリック標準の XML for Analysis (XMLA) を使用します。 クライアント オブジェクト モデルも XMLA 経由で提供されます。クライアント オブジェクト モデルには、ADOMD.NET などのマネージ プロバイダーまたはネイティブ OLE DB プロバイダーを使用してアクセスできます。  
  
-   クエリ コマンドは、SQL、分析用の業界標準クエリ言語である多次元式 (MDX)、またはデータ マイニング指向の業界標準クエリ言語であるデータ マイニング拡張機能 (DMX) を使用して発行できます。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベース オブジェクトの管理には、Analysis Services スクリプト言語 (ASSL) を使用することもできます。  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、接続されていないクライアント上のアプリケーションがローカルに格納された多次元データを参照することを可能にするローカル キューブ エンジンもサポートされます。 詳細については、次を参照してください[Analysis Services 開発用のクライアント アーキテクチャの要件。](../../../analysis-services/multidimensional-models/olap-physical/client-architecture-requirements-for-analysis-services-development.md)  
  
## <a name="in-this-section"></a>このセクションの内容  
 **論理アーキテクチャの概要**  
 [論理アーキテクチャの概要 &#40;です。Analysis Services - 多次元データ &#41;](../../../analysis-services/multidimensional-models/olap-logical/logical-architecture-overview-analysis-services-multidimensional-data.md)  
  
 **Server オブジェクト**  
 [サーバー オブジェクト &#40;です。Analysis Services - 多次元データ &#41;](../../../analysis-services/multidimensional-models/olap-logical/server-objects-analysis-services-multidimensional-data.md)  
  
 **データベース オブジェクト**  
 [データベース オブジェクト &#40;です。Analysis Services - 多次元データ &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
 **Dimension オブジェクト**  
 [ディメンション オブジェクト &#40;です。Analysis Services - 多次元データ &#41;](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 **キューブ オブジェクト**  
 [キューブ オブジェクト &#40;です。Analysis Services - 多次元データ &#41;](../../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 **ユーザー アクセス セキュリティ**  
 [ユーザー アクセス セキュリティ アーキテクチャ](http://msdn.microsoft.com/library/71b44e10-2bd0-44f7-8de9-7c8f5b7ac082)  
  
## <a name="see-also"></a>参照  
 [Microsoft OLAP アーキテクチャをについてください。](../../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)   
 [物理アーキテクチャ &#40;です。Analysis Services - 多次元データ &#41;](../../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-physical-architecture.md)  
  
  
