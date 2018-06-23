---
title: 論理アーキテクチャ (Analysis Services - 多次元データ) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- logical architecture [Analysis Services Multidimensional Data]
ms.assetid: 1b9cae0a-8990-4194-af5f-a1ea5f2aff06
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 468ad4b5f7456524b4d44552bd18cf80406bee07
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165113"
---
# <a name="logical-architecture-analysis-services---multidimensional-data"></a>論理アーキテクチャ (Analysis Services - 多次元データ)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーとクライアントの両方のコンポーネントを使用して、オンライン分析処理 (OLAP) とビジネス インテリジェンス アプリケーション用のデータ マイニング機能を指定します。  
  
-   [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のサーバー コンポーネントは、Microsoft Windows サービスとして実装されます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 各インスタンスと、同じコンピューターに複数のインスタンスをサポートしている[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]Windows サービスの個別のインスタンスとして実装します。  
  
-   クライアントは、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] との通信に、コマンドの発行や応答の受信のための SOAP ベースのプロトコルで、Web サービスとして公開されているパブリック標準の XML for Analysis (XMLA) を使用します。 クライアント オブジェクト モデルも XMLA 経由で提供されます。クライアント オブジェクト モデルには、ADOMD.NET などのマネージ プロバイダーまたはネイティブ OLE DB プロバイダーを使用してアクセスできます。  
  
-   クエリ コマンドは、SQL、分析用の業界標準クエリ言語である多次元式 (MDX)、またはデータ マイニング指向の業界標準クエリ言語であるデータ マイニング拡張機能 (DMX) を使用して発行できます。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベース オブジェクトの管理には、Analysis Services スクリプト言語 (ASSL) を使用することもできます。  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、接続されていないクライアント上のアプリケーションがローカルに格納された多次元データを参照することを可能にするローカル キューブ エンジンもサポートされます。 詳細については、次を参照してください[Analysis Services 開発用のクライアント アーキテクチャの要件。](../olap-physical/client-architecture-requirements-for-analysis-services-development.md)  
  
## <a name="in-this-section"></a>このセクションの内容  
 **論理アーキテクチャの概要**  
 [論理アーキテクチャの概要&#40;Analysis Services - 多次元データ&#41;](logical-architecture-overview-analysis-services-multidimensional-data.md)  
  
 **サーバー オブジェクト**  
 [サーバー オブジェクト&#40;Analysis Services - 多次元データ&#41;](server-objects-analysis-services-multidimensional-data.md)  
  
 **データベース オブジェクト**  
 [データベース オブジェクト&#40;Analysis Services - 多次元データ&#41;](database-objects-analysis-services-multidimensional-data.md)  
  
 **ディメンション オブジェクト**  
 [ディメンション オブジェクト&#40;Analysis Services - 多次元データ&#41;](../../multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 **キューブ オブジェクト**  
 [キューブ オブジェクト&#40;Analysis Services - 多次元データ&#41;](../../multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 **ユーザー アクセス セキュリティ**  
 [ユーザー アクセス セキュリティ アーキテクチャ](https://msdn.microsoft.com/library/bb522595(SQL.120).aspx)  
  
## <a name="see-also"></a>参照  
 [Microsoft OLAP アーキテクチャをについてください。](../olap-physical/understanding-microsoft-olap-architecture.md)   
 [物理アーキテクチャ&#40;Analysis Services - 多次元データ&#41;](../olap-physical/understanding-microsoft-olap-physical-architecture.md)  
  
  