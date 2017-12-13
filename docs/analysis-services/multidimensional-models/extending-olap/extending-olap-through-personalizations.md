---
title: "パーソナル化による OLAP の拡張 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: Analysis Services, extensibility
ms.assetid: 348e49fc-4390-43c1-9b6c-61b386ff4373
caps.latest.revision: "10"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e41858ee929aa38bc043939378f45d35eac755dd
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="extending-olap-through-personalizations"></a>パーソナル化による OLAP の拡張
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Analysis Services は、多次元式 (MDX) およびデータ マイニング拡張機能 (DMX) 言語で使用する多くの組み込み関数を提供します。 これらの関数は、標準的な統計計算から階層に含まれるメンバーのスキャンまで、さまざまな処理に対応できるように設計されています。 ただしと同様に、他の複雑で強力な製品は常にこのような製品のさらに機能を拡張する必要があります。  
  
 そのため、Analysis Services は、標準機能だけでは満たすことのできないビジネス ニーズを補うために、サービスのインスタンスにアセンブリやパーソナル化された拡張機能を追加できるようになっています。  
  
## <a name="assemblies"></a>アセンブリ  
 アセンブリにより、MDX と DMX のビジネス機能の拡張が可能になります。 必要な機能をダイナミック リンク ライブラリ (DLL) などのライブラリとして作成し、このライブラリをアセンブリとして Analysis Services のインスタンスまたは Analysis Services データベースに追加します。 ライブラリ内のパブリック メソッドは、ユーザー定義関数として、MDX および DMX 式、プロシージャ、計算、動作、およびクライアント アプリケーションに公開されます。  
  
## <a name="personalized-extensions"></a>パーソナル化拡張機能  
 SQL Server Analysis Services のパーソナル化拡張機能は、プラグイン アーキテクチャを実装するという概念の基盤です。 Analysis Services のパーソナル化拡張機能は、既存のマネージ アセンブリ アーキテクチャに対する単純で簡潔な変更で、Analysis Services の <xref:Microsoft.AnalysisServices.AdomdServer> オブジェクト モデル、多次元式 (MDX) 構文、およびスキーマ行セット全体で公開されます。  
  
## <a name="see-also"></a>参照  
 [多次元モデルのアセンブリの管理](../../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Analysis Services のパーソナル化拡張機能](../../../analysis-services/multidimensional-models/extending-olap/analysis-services-personalization-extensions.md)  
  
  
