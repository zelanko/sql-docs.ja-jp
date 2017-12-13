---
title: "分析の使用による開発 Services スクリプト言語 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
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
helpviewer_keywords:
- Analysis Services Scripting Language
- ASSL
ms.assetid: ce9aca4d-b7ad-451e-bb7f-20c2b0c03f29
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 45b116586a0ce328815d8139b751547045fa85f8
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="developing-with-analysis-services-scripting-language-assl"></a>Analysis Services スクリプト言語 (ASSL) での開発
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Analysis Services スクリプト言語 (ASSL) は、オブジェクト定義言語とコマンド言語の作成と管理サーバー上で直接 Analysis Services 構造を追加する XMLA の拡張機能です。 ASSL をカスタム アプリケーションで使用して、XMLA プロトコルで Analysis Services と通信できます。 ASSL は次の 2 つの部分で構成されます。  
  
-   データ定義言語 (DDL) またはオブジェクト定義言語を定義しのインスタンスを記述[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]、だけでなく、データベースおよびインスタンスが含まれているデータベース オブジェクトです。  
  
-   などのアクション コマンドを送信するコマンド言語**作成**、 **Alter**、または**プロセス**、Analysis Services のインスタンスにします。 このコマンド言語については、 [XML for Analysis &#40;です。XMLA &#41;参照](../../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)です。  
  
 [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)] で多次元ソリューションを構成する ASSL を表示するには、プロジェクト レベルで [コードの表示] を使用します。 XMLA クエリ エディターを使用して、[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] で ASSL スクリプトを作成または編集することもできます。 作成したスクリプトは、サーバーでのオブジェクトの管理やコマンドの実行に使用できます。  
  
## <a name="see-also"></a>参照  
 [ASSL オブジェクトとオブジェクトの特性](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-objects-and-object-characteristics.md)   
 [ASSL XML 規則](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-xml-conventions.md)   
 [データ ソースとのバインド &#40;です。SSAS 多次元 &#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)  
  
  
