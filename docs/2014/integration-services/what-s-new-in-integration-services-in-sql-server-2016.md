---
title: どのような&#39;s 新しい (Integration Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, what's new
- what's new [Integration Services]
ms.assetid: da6999c7-e5e3-4a59-a284-1da635995af1
caps.latest.revision: 112
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 39b6e64dbf6add0b026e384432059875cf724507
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37221682"
---
# <a name="what39s-new-integration-services"></a>どのような&#39;s 新しい (Integration Services)
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] は、以前のリリースから変更されていません。  
  
 については、[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]製品およびテクノロジでは、「 [SQL Server 2014 における新](../sql-server/what-s-new-in-sql-server-2016.md)します。  
  
 関連する変更の詳細については[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Business Intelligence を参照してください[Analysis Services と Business Intelligence で新](../analysis-services/what-s-new-in-analysis-services.md)します。  
  
##  <a name="ValidateXML"></a> XML タスクでの XML 検証の詳細な出力  
 XML ドキュメントを検証し、有効にすると詳細なエラー出力を取得、 `ValidationDetails` XML タスクのプロパティ。 前に、`ValidationDetails`プロパティが使用可能な XML タスクによる XML 検証にのみ、true または false の結果、エラーやその場所に関する情報が返されます。 次に、設定`ValidationDetails`を true に、出力ファイルに行番号と位置を含むすべてのエラーに関する詳細情報が含まれています。 この情報を使って、XML ドキュメントのエラーを把握、特定、修正できます。 詳細については、「 [Validate XML with the XML Task](control-flow/xml-task.md)」を参照してください。  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] 導入された、`ValidationDetails`プロパティ[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]Service Pack 2。 その時点では、この新しいプロパティは発表されることも文書化されることもありませんでした。 `ValidationDetails`で使用可能なプロパティも[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]と SQL Server 2016 でします。  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 の各エディションがサポートする機能](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  
