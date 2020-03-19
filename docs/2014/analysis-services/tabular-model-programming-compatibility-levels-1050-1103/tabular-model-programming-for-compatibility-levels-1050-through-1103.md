---
title: テーブルモデルのプログラミング |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 0ceb461e-12c1-44ea-97ac-b99bf308676b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1c9b04245e14be67242d5cd1ea6d257ac4fc6038
ms.sourcegitcommit: 36d07f0b832b1b29df6ffbfebc8c60016b37f5cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/18/2020
ms.locfileid: "79525433"
---
# <a name="tabular-model-programming"></a>テーブル モデルのプログラミング
  テーブル モデルでは、リレーショナル構造を使用して、分析アプリケーションおよびレポート アプリケーションによって使用される Analysis Services のデータがモデル化されます。 これらのモデルは、ストレージ用のメモリ内分析エンジンおよび要求に応じてデータを集計して計算する高速テーブル スキャンを使用して、テーブル モード用に構成された Analysis Service インスタンスで実行されます。  
  
 プログラム的には、AMO、ADOMD.NET、XMLA、または OLE DB で使用するオブジェクトは、テーブル ソリューションでも多次元ソリューションでも基本的に同じです。 カスタム BI ソリューションの要件がテーブル モデル データベースによって最もよく満たされる場合は、任意の Analysis Services クライアント ライブラリおよびプログラミング インターフェイスを使用して、アプリケーションと Analysis Services インスタンス上のテーブル モデルを統合できます。 テーブル モデルのデータをクエリおよび計算するには、組み込まれた MDX または DAX をコードで使用できます。  
  
 ここでは、テーブル モデル エンティティとそのプロパティをプログラムで操作する方法について詳しく説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ビジネスインテリジェンス &#40;CSDLBI&#41;の CSDL 注釈](/analysis-services/csdlbi/csdl-annotations-for-business-intelligence-csdlbi)  
  
 [テーブル オブジェクト モデルについて](representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
 [CSDL への BI 注釈のテクニカルリファレンス](/analysis-services/csdlbi/technical-reference-for-bi-annotations-to-csdl)  
  
 [IMDEmbedded インターフェイス](imdembeddeddata-interface.md)  
  
## <a name="see-also"></a>参照  
 [SSAS 表形式&#41;の表形式モデル &#40;](../tabular-models/tabular-models-ssas.md)   
 [SSAS 表形式&#41;&#40;テーブルモデルデザイナー](../tabular-model-designer-ssas-tabular.md)  
  
  
