---
title: Analysis Services Database | のドキュメントとスクリプトの作成 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- XML for Analysis, scripts
- XMLA, scripts
- scripts [Analysis Services], databases
- documenting databases
- databases [Analysis Services], documenting
- databases [Analysis Services], scripts
ms.assetid: 125044e2-8d36-4733-8743-8bb68ff9aa4e
author: minewiskan
ms.author: owend
ms.openlocfilehash: cfe008b0d6903d7d012eb57d41d6e50240202ec8
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546794"
---
# <a name="document-and-script-an-analysis-services-database"></a>Analysis Services データベースのドキュメントとスクリプトの作成
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを配置した後、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、データベースのメタデータまたはデータベースに含まれているオブジェクトのメタデータを XML for Analysis (XMLA) スクリプトとして出力できます。 このスクリプトは、新しい **[XMLA クエリ エディター]** ウィンドウ、ファイル、またはクリップボードに出力できます。 XMLA の詳細については、「 [Analysis Services Scripting Language &#40;ASSL&#41; リファレンス](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)」を参照してください。  
  
 生成された XMLA スクリプトでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] スクリプト言語 (ASSL) の要素を使用して、スクリプトに含まれるオブジェクトを定義します。 CREATE スクリプトを生成した場合、結果として得られる XMLA スクリプトには、インスタンスで **データベース構造全体を作成するための XMLA** Create [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コマンドおよび ASSL 要素が含まれます。 ALTER スクリプトを生成した場合、結果として得られる XMLA スクリプトには、既存の **データベースの構造をスクリプト作成時点のデータベースの状態に復元するための XMLA** Alter [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コマンドおよび ASSL 要素が含まれます。  
  
 生成された XMLA スクリプトは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースから以下のようなさまざまな用途に使用できます。  
  
-   すべてのデータベース オブジェクトおよび権限を再作成するためのバックアップ スクリプトを維持できます。  
  
-   データベース開発コードを作成または更新できます。  
  
-   既存のスキーマからテスト環境または開発環境を作成できます。  
  
## <a name="see-also"></a>参照  
 [Analysis Services データベースを変更または削除する](modify-or-delete-an-analysis-services-database.md)   
 [XMLA&#41;の Alter 要素 &#40;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)   
 [Create 要素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)  
  
  
