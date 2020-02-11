---
title: Analysis Services Scripting Language (ASSL) を使用した開発 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services Scripting Language
- ASSL
ms.assetid: ce9aca4d-b7ad-451e-bb7f-20c2b0c03f29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dfdce0d0db35d651d12670ffd3cb1c9437961cd1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62736519"
---
# <a name="developing-with-analysis-services-scripting-language-assl"></a>Analysis Services スクリプト言語 (ASSL) での開発
  Analysis Services スクリプト言語 (ASSL) は、Analysis Services 構造をサーバーで直接作成および管理するためのオブジェクト定義言語とコマンド言語を追加する、XMLA の拡張機能です。 ASSL をカスタム アプリケーションで使用して、XMLA プロトコルで Analysis Services と通信できます。 ASSL は次の 2 つの部分で構成されます。  
  
-   データ定義言語 (DDL) またはオブジェクト定義言語は、の[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス、およびインスタンスに含まれるデータベースおよびデータベースオブジェクトを定義し、記述します。  
  
-   
  `Create`、`Alter`、`Process` などのアクション コマンドを Analysis Services のインスタンスに送信するコマンド言語。 このコマンド言語については、「 [XML for Analysis &#40;XMLA&#41; リファレンス](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)」で説明されています。  
  
 
  [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)] で多次元ソリューションを構成する ASSL を表示するには、プロジェクト レベルで [コードの表示] を使用します。 XMLA クエリ エディターを使用して、[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] で ASSL スクリプトを作成または編集することもできます。 作成したスクリプトは、サーバーでのオブジェクトの管理やコマンドの実行に使用できます。  
  
## <a name="see-also"></a>参照  
 [ASSL オブジェクトとオブジェクトの特性](assl-objects-and-object-characteristics.md)   
 [ASSL XML 規則](assl-xml-conventions.md)   
 [SSAS 多次元&#41;&#40;データソースとバインド](../data-sources-and-bindings-ssas-multidimensional.md)  
  
  
