---
title: "文書化し、Analysis Services データベースのスクリプトを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML for Analysis, scripts
- XMLA, scripts
- scripts [Analysis Services], databases
- documenting databases
- databases [Analysis Services], documenting
- databases [Analysis Services], scripts
ms.assetid: 125044e2-8d36-4733-8743-8bb68ff9aa4e
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bf7f3de5da4b7477ba27fd3f46a8627ac94aedb2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="document-and-script-an-analysis-services-database"></a>Analysis Services データベースのドキュメントとスクリプトの作成
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを配置した後、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、データベースのメタデータまたはデータベースに含まれているオブジェクトのメタデータを XML for Analysis (XMLA) スクリプトとして出力できます。 このスクリプトは、新しい **[XMLA クエリ エディター]** ウィンドウ、ファイル、またはクリップボードに出力できます。 XMLA の詳細については、「[Analysis Services スクリプト言語 (XMLA 用 ASSL)](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)」を参照してください。  
  
 生成された XMLA スクリプトでは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] スクリプト言語 (ASSL) の要素を使用して、スクリプトに含まれるオブジェクトを定義します。 CREATE スクリプトを生成した場合、結果として得られる XMLA スクリプトには、インスタンスで **データベース構造全体を作成するための XMLA** Create [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コマンドおよび ASSL 要素が含まれます。 ALTER スクリプトを生成した場合、結果として得られる XMLA スクリプトには、既存の **データベースの構造をスクリプト作成時点のデータベースの状態に復元するための XMLA** Alter [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コマンドおよび ASSL 要素が含まれます。  
  
 生成された XMLA スクリプトは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースから以下のようなさまざまな用途に使用できます。  
  
-   すべてのデータベース オブジェクトおよび権限を再作成するためのバックアップ スクリプトを維持できます。  
  
-   データベース開発コードを作成または更新できます。  
  
-   既存のスキーマからテスト環境または開発環境を作成できます。  
  
## <a name="see-also"></a>参照  
 [Analysis Services データベースの変更または削除](../../analysis-services/multidimensional-models/modify-or-delete-an-analysis-services-database.md)   
 [Alter 要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)   
 [要素 &#40; を作成します。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)  
  
  
