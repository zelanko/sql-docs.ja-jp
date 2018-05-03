---
title: 文書化し、Analysis Services データベースのスクリプトを作成 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 645499bc5311f74ba689b3cd48d2516c01d384fb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="document-and-script-an-analysis-services-database"></a>Analysis Services データベースのドキュメントとスクリプトの作成
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを配置した後、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、データベースのメタデータまたはデータベースに含まれているオブジェクトのメタデータを XML for Analysis (XMLA) スクリプトとして出力できます。 このスクリプトは、新しい **[XMLA クエリ エディター]** ウィンドウ、ファイル、またはクリップボードに出力できます。 XMLA の詳細については、「[Analysis Services スクリプト言語 (XMLA 用 ASSL)](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)」を参照してください。  
  
 生成された XMLA スクリプトでは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] スクリプト言語 (ASSL) の要素を使用して、スクリプトに含まれるオブジェクトを定義します。 CREATE スクリプトを生成した場合、結果として得られる XMLA スクリプトには、インスタンスで **データベース構造全体を作成するための XMLA** Create [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コマンドおよび ASSL 要素が含まれます。 ALTER スクリプトを生成した場合、結果として得られる XMLA スクリプトには、既存の **データベースの構造をスクリプト作成時点のデータベースの状態に復元するための XMLA** Alter [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コマンドおよび ASSL 要素が含まれます。  
  
 生成された XMLA スクリプトは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースから以下のようなさまざまな用途に使用できます。  
  
-   すべてのデータベース オブジェクトおよび権限を再作成するためのバックアップ スクリプトを維持できます。  
  
-   データベース開発コードを作成または更新できます。  
  
-   既存のスキーマからテスト環境または開発環境を作成できます。  
  
## <a name="see-also"></a>参照  
 [Analysis Services データベースの変更または削除](../../analysis-services/multidimensional-models/modify-or-delete-an-analysis-services-database.md)   
 [Alter 要素&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)   
 [要素を作成する&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)  
  
  
