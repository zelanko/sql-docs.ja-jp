---
title: 分析の使用による開発 Services スクリプト言語 (ASSL) |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d1c01f567599353d360d8cf4a213e2abaa6c6cff
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34025839"
---
# <a name="developing-with-analysis-services-scripting-language-assl"></a>Analysis Services スクリプト言語 (ASSL) での開発
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Analysis Services スクリプト言語 (ASSL) は、Analysis Services 構造をサーバーで直接作成および管理するためのオブジェクト定義言語とコマンド言語を追加する、XMLA の拡張機能です。 ASSL をカスタム アプリケーションで使用して、XMLA プロトコルで Analysis Services と通信できます。 ASSL は次の 2 つの部分で構成されます。  
  
-   データ定義言語 (DDL) またはオブジェクト定義言語を定義しのインスタンスを記述[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]、だけでなく、データベースおよびインスタンスが含まれているデータベース オブジェクトです。  
  
-   などのアクション コマンドを送信するコマンド言語**作成**、 **Alter**、または**プロセス**、Analysis Services のインスタンスにします。 このコマンド言語については、 [XML for Analysis &#40;XMLA&#41;参照](../../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)です。  
  
 [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)] で多次元ソリューションを構成する ASSL を表示するには、プロジェクト レベルで [コードの表示] を使用します。 XMLA クエリ エディターを使用して、[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] で ASSL スクリプトを作成または編集することもできます。 作成したスクリプトは、サーバーでのオブジェクトの管理やコマンドの実行に使用できます。  
  
## <a name="see-also"></a>参照  
 [ASSL オブジェクトとオブジェクトの特性](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-objects-and-object-characteristics.md)   
 [ASSL XML 規則](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-xml-conventions.md)   
 [データ ソースとのバインド & #40 です。SSAS 多次元 & #41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)  
  
  
