---
title: Analysis Services データ マイニングのプログラミング |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1b4068d012b64cb4fc5352ed11c8576a38d6d6c4
ms.sourcegitcommit: 603d5ef9b45c2f111d36d11864dc032917e4a321
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65450121"
---
# <a name="data-mining-programming"></a>データ マイニングのプログラミング
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の組み込みのツールやビューアーが要件を満たしていない場合は、独自の拡張機能をコーディングすることによって [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の機能を拡張できます。 この方法では、2 つのオプションがあります。  
  
-   **XMLA**  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] クライアント アプリケーションとの通信用プロトコルとして XML for Analysis (XMLA) をサポートします。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、XML for Analysis 仕様を拡張する追加のコマンドをサポートしています。  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ではデータ定義、データ操作、およびデータ制御サポートに XMLA を使用するため、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] に用意されているビジュアル ツールを使用してマイニング構造とマイニング モデルを作成し、データ マイニング拡張機能 (DMX) と Analysis Services スクリプト言語 (ASSL) のスクリプトを使用して作成したデータ マイニング オブジェクトを拡張できます。  
  
     データ マイニング オブジェクトを XMLA スクリプトだけで作成および変更できます。また、プログラムを使用して、独自のアプリケーションからモデルに対して予測クエリを実行できます。  
  
-   **分析管理オブジェクト (AMO)**  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には、サード パーティのデータ マイニング プロバイダーがデータ マイニング オブジェクトを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に統合できるようにする完全なフレームワークも用意されています。  
  
     AMO を使用して、マイニング構造とマイニング モデルを作成できます。 CodePlex の次のサンプルを参照してください。  
  
    -   [AMO ブラウザー]  
  
         指定した SSAS インスタンスに接続し、マイニング構造とマイニング モデルを含め、すべてのサーバー オブジェクトとそれらのプロパティを一覧表示します。  
  
    -   AMO の簡単な例  
  
         AS Simple サンプルは、ほとんどの主要なオブジェクトに対するプログラムによるアクセスを取り扱い、メタデータの参照方法やオブジェクト内の値へのアクセス方法を示します。  
  
         このサンプルでは、データ マイニング構造とモデルを作成して操作する方法や、既存のデータ マイニング モデルを参照する方法も示します。  
  
-   **DMX**  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーへの接続を作成したことを前提とすると、DMX を使用して、コマンド ステートメント、予測クエリ、およびメタデータ クエリをカプセル化し、表形式で結果を返すことができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [OLE DB for Data Mining](data-mining-programming-ole-db.md)  
 データ マイニングと多次元データをサポートするための仕様への追加項目として、新しいスキーマ行セットと列、およびマイニング構造の作成と管理のためのデータ マイニング拡張機能 (DMX) 言語について説明します。  
  
## <a name="related-reference"></a>関連リファレンス  
 [ADOMD.NET での開発](https://docs.microsoft.com/bi-reference/adomd/developing-with-adomd-net)  
 ADOMD.NET クライアントおよびサーバー プログラミング オブジェクトについて説明します。  
  
 [分析管理オブジェクト &#40;AMO&#41; による開発](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)  
 AMO プログラミング ライブラリについて説明します。  
  
 [Analysis Services スクリプト言語 (ASSL) での開発](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)  
 XML for Analysis (XMLA) とその拡張機能について説明します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services Developer Documentation (Analysis Services の開発者向けドキュメント)](../analysis-services-developer-documentation.md)   
 [データ マイニング拡張機能 &#40;DMX&#41; リファレンス](../../dmx/data-mining-extensions-dmx-reference.md)  
  
  
