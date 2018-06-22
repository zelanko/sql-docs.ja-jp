---
title: どのような&#39;s (Integration Services) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Integration Services, what's new
- what's new [Integration Services]
ms.assetid: da6999c7-e5e3-4a59-a284-1da635995af1
caps.latest.revision: 112
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c7d37fb3c1d2cd1dcafecc012fbe83e1864e50ed
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072126"
---
# <a name="what39s-new-integration-services"></a>どのような&#39;s (Integration Services)
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] は、以前のリリースから変更されていません。  
  
 その他の方法について[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]製品およびテクノロジを参照してください。 [SQL Server 2014 の新](../sql-server/what-s-new-in-sql-server-2016.md)です。  
  
 関連する変更の詳細については[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Business Intelligence を参照してください[Analysis Services と Business Intelligence の新](../analysis-services/what-s-new-in-analysis-services.md)です。  
  
##  <a name="ValidateXML"></a> XML タスクでの XML 検証の詳細な出力  
 XML ドキュメントを検証し、有効にすると詳細なエラー出力を取得、 `ValidationDetails` XML タスクのプロパティです。 前に、`ValidationDetails`プロパティが使用可能な XML タスクによる XML 検証にのみ、true または false の結果、エラーやその場所に関する情報が返されます。 これで、設定`ValidationDetails`を true に、出力ファイルに行番号と位置を含むすべてのエラーに関する詳細情報が含まれています。 この情報を使って、XML ドキュメントのエラーを把握、特定、修正できます。 詳細については、「 [Validate XML with the XML Task](control-flow/xml-task.md)」を参照してください。  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] 導入された、`ValidationDetails`プロパティ[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]Service Pack 2 です。 その時点では、この新しいプロパティは発表されることも文書化されることもありませんでした。 `ValidationDetails`で利用可能なプロパティも[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]と SQL Server 2016 でします。  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 の各エディションがサポートする機能](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  