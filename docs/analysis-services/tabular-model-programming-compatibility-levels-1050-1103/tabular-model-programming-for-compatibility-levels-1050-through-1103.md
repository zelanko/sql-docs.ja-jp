---
title: 互換性のためのテーブル モデルのプログラミング レベル 1103 を通じて 1050 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0ceb461e-12c1-44ea-97ac-b99bf308676b
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 99d03c35c9f50d0d232814300f5a07bed289d47e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="tabular-model-programming-for-compatibility-levels-1050-through-1103"></a>互換性のためのテーブル モデルのプログラミング レベルを 1050 から 1103
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  テーブル モデルでは、リレーショナル構造を使用して、分析アプリケーションおよびレポート アプリケーションによって使用される Analysis Services のデータがモデル化されます。 これらのモデルは、ストレージ用のメモリ内分析エンジンおよび要求に応じてデータを集計して計算する高速テーブル スキャンを使用して、テーブル モード用に構成された Analysis Service インスタンスで実行されます。  
  
 カスタム BI ソリューションの要件がテーブル モデル データベースによって最もよく満たされる場合は、任意の Analysis Services クライアント ライブラリおよびプログラミング インターフェイスを使用して、アプリケーションと Analysis Services インスタンス上のテーブル モデルを統合できます。 テーブル モデルのデータをクエリおよび計算するには、組み込まれた MDX または DAX をコードで使用できます。  
  
 互換性レベル 1103、を通じて 1050 で特定のモデルでの Analysis Services の以前のバージョンで作成されたテーブル モデル AMO、ADOMD.NET、XMLA、または OLE DB でプログラムで使用するオブジェクトは、表形式の両方の根本的に同じと多次元ソリューションです。 具体的には、多次元モデルに対して定義されているオブジェクトのメタデータは、表形式モデルの互換性レベル 1050 ~ 1103 にも使用されます。  
  
 SQL Server 2016 以降では、表形式モデル構築したりを表形式のメタデータを使用して、モデルの定義を 1200 以上の互換性レベルにアップグレードします。 メタデータとプログラミングは、このレベルでは基本的に異なります。 参照してください[互換性レベル 1200 以降、表形式のモデルにプログラミング](../../analysis-services/tabular-model-programming-compatibility-level-1200/tabular-model-programming-for-compatibility-level-1200.md)と[Analysis Services のアップグレード](../../database-engine/install-windows/upgrade-analysis-services.md)詳細についてはします。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Business Intelligence & #40; 向けの CSDL 注釈CSDLBI & #41;](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdl-annotations-for-business-intelligence-csdlbi.md)  
  
 [レベルを 1050 から 1103 表形式オブジェクト モデルの互換性を理解します。](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
 [CSDL への BI 注釈のテクニカル リファレンス](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  

[IMDEmbeddedData インターフェイス](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/imdembeddeddata-interface.md)


  
  
