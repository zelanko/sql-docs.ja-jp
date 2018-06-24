---
title: 分析の使用による開発 Services スクリプト言語 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Analysis Services Scripting Language
- ASSL
ms.assetid: ce9aca4d-b7ad-451e-bb7f-20c2b0c03f29
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e7cc4d26ca41b36bc1472417d64702345911ceec
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074485"
---
# <a name="developing-with-analysis-services-scripting-language-assl"></a>Analysis Services スクリプト言語 (ASSL) での開発
  Analysis Services スクリプト言語 (ASSL) は、Analysis Services 構造をサーバーで直接作成および管理するためのオブジェクト定義言語とコマンド言語を追加する、XMLA の拡張機能です。 ASSL をカスタム アプリケーションで使用して、XMLA プロトコルで Analysis Services と通信できます。 ASSL は次の 2 つの部分で構成されます。  
  
-   データ定義言語 (DDL) またはオブジェクト定義言語を定義しのインスタンスを記述[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]、だけでなく、データベースおよびインスタンスが含まれているデータベース オブジェクトです。  
  
-   `Create`、`Alter`、`Process` などのアクション コマンドを Analysis Services のインスタンスに送信するコマンド言語。 このコマンド言語については、 [XML for Analysis &#40;XMLA&#41;参照](../../xmla/xml-for-analysis-xmla-reference.md)です。  
  
 [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)] で多次元ソリューションを構成する ASSL を表示するには、プロジェクト レベルで [コードの表示] を使用します。 XMLA クエリ エディターを使用して、[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] で ASSL スクリプトを作成または編集することもできます。 作成したスクリプトは、サーバーでのオブジェクトの管理やコマンドの実行に使用できます。  
  
## <a name="see-also"></a>参照  
 [ASSL オブジェクトとオブジェクトの特性](assl-objects-and-object-characteristics.md)   
 [ASSL XML 規則](assl-xml-conventions.md)   
 [データ ソースとバインド&#40;SSAS 多次元&#41;](../data-sources-and-bindings-ssas-multidimensional.md)  
  
  