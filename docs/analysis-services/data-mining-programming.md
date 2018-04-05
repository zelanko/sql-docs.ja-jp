---
title: データ マイニングのプログラミング |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- data mining [Analysis Services], developer's guide
ms.assetid: 9fd77b16-0b89-44ce-bcf1-7c04b62499da
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 38db9eddac7c7b753b680714f53d6ad01a49ea00
ms.sourcegitcommit: 82c9868b5bf95e5b0c68137ba434ddd37fc61072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="data-mining-programming"></a>データ マイニングのプログラミング
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の組み込みのツールやビューアーが要件を満たしていない場合は、独自の拡張機能をコーディングすることによって [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の機能を拡張できます。 この方法では、次の 2 つのオプションがあります。  
  
-   **XMLA**  
  
     [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]クライアント アプリケーションとの通信用プロトコルとして XML for Analysis (XMLA) をサポートします。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] では、XML for Analysis 仕様を拡張する追加のコマンドをサポートしています。  
  
     [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ではデータ定義、データ操作、およびデータ制御サポートに XMLA を使用するため、[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] に用意されているビジュアル ツールを使用してマイニング構造とマイニング モデルを作成し、データ マイニング拡張機能 (DMX) と Analysis Services スクリプト言語 (ASSL) のスクリプトを使用して作成したデータ マイニング オブジェクトを拡張できます。  
  
     データ マイニング オブジェクトを XMLA スクリプトだけで作成および変更できます。また、プログラムを使用して、独自のアプリケーションからモデルに対して予測クエリを実行できます。  
  
-   **分析管理オブジェクト (AMO)**  
  
     [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] には、サード パーティのデータ マイニング プロバイダーがデータ マイニング オブジェクトを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] に統合できるようにする完全なフレームワークも用意されています。  
  
     AMO を使用して、マイニング構造とマイニング モデルを作成できます。 CodePlex の次のサンプルを参照してください。  
  
    -   [AMO ブラウザー]  
  
         指定した SSAS インスタンスに接続し、マイニング構造とマイニング モデルを含め、すべてのサーバー オブジェクトとそれらのプロパティを一覧表示します。  
  
    -   AMO の簡単な例  
  
         AS Simple サンプルは、ほとんどの主要なオブジェクトに対するプログラムによるアクセスを取り扱い、メタデータの参照方法やオブジェクト内の値へのアクセス方法を示します。  
  
         このサンプルでは、データ マイニング構造とモデルを作成して操作する方法や、既存のデータ マイニング モデルを参照する方法も示します。  
  
-   **DMX**  
  
     [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーへの接続を作成したことを前提とすると、DMX を使用して、コマンド ステートメント、予測クエリ、およびメタデータ クエリをカプセル化し、表形式で結果を返すことができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [OLE DB for Data Mining](../analysis-services/data-mining-programming-ole-db.md)  
 データ マイニングと多次元データをサポートするための仕様への追加項目として、新しいスキーマ行セットと列、およびマイニング構造の作成と管理のためのデータ マイニング拡張機能 (DMX) 言語について説明します。  
  
## <a name="related-reference"></a>関連リファレンス  
 [ADOMD.NET での開発](../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)  
 ADOMD.NET クライアントおよびサーバー プログラミング オブジェクトについて説明します。  
  
 [分析管理オブジェクト &#40; を使用した開発AMO &#41;](../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)  
 AMO プログラミング ライブラリについて説明します。  
  
 [Analysis Services スクリプト言語 &#40; を使用した開発ASSL &#41;](../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
 XML for Analysis (XMLA) とその拡張機能について説明します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services Developer Documentation (Analysis Services の開発者向けドキュメント)](../analysis-services/analysis-services-developer-documentation.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;参照](../dmx/data-mining-extensions-dmx-reference.md)  
  
  
