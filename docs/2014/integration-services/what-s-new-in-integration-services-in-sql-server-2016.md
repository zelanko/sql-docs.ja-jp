---
title: '&#39;の新機能 (Integration Services) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, what's new
- what's new [Integration Services]
ms.assetid: da6999c7-e5e3-4a59-a284-1da635995af1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5562b7424e4a104204becaed10378ffc999c4e98
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68891106"
---
# <a name="what39s-new-integration-services"></a>新機能 (Integration Services)&#39;
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]は、以前のリリースから変更されていません。  
  
 その他の[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]製品とテクノロジの詳細については、「 [SQL Server 2014 の新機能](../sql-server/what-s-new-in-sql-server-2016.md)」を参照してください。  
  
 ビジネスインテリジェンスに関連する[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]変更の詳細については、「 [Analysis Services とビジネスインテリジェンスの新機能](https://docs.microsoft.com/analysis-services/what-s-new-in-analysis-services)」を参照してください。  
  
##  <a name="ValidateXML"></a>XML タスクでの豊富な XML 検証出力  
 XML タスクの `ValidationDetails` プロパティを有効にして、XML ドキュメントを検証し、詳細なエラー出力を取得します。 
  `ValidationDetails` プロパティが利用できるようになる前は、XML タスクによる XML 検証では、true や false のみの結果が返され、エラーやその場所に関する情報は返されませんでした。 これで、を true `ValidationDetails`に設定すると、出力ファイルには、行番号と位置を含むすべてのエラーに関する詳細情報が含まれるようになりました。 この情報を使って、XML ドキュメントのエラーを把握、特定、修正できます。 詳細については、「 [Validate XML with the XML Task](control-flow/xml-task.md)」を参照してください。  
  
 
  [!INCLUDE[ssIS](../includes/ssis-md.md)] では、`ValidationDetails` Service Pack 2 で [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] プロパティが導入されました。 その時点では、この新しいプロパティは発表されることも文書化されることもありませんでした。 
  `ValidationDetails` プロパティは、[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] と SQL Server 2016 でも利用できます。  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 の各エディションがサポートする機能](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  
