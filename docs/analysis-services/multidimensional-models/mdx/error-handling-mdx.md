---
title: "エラー処理 (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scripts [MDX], exceptions
- exceptions [MDX]
ms.assetid: bc6ff0af-9fe6-44d6-bc3c-801d71ea41a9
caps.latest.revision: 26
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bbd604d132fa204da606b44d72551f198661c81a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="error-handling-mdx"></a>エラー処理 (MDX)
  各キューブでは、多次元式 (MDX) スクリプト内のエラーの処理方法を制御できます。 エラー処理は、 **ScriptErrorHandlingMode** 列挙子を通して実行されます。 この列挙子は、以下のいずれかの値をとります。  
  
 **IgnoreNone**  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] が MDX スクリプト内になんらかのエラーを検出した場合、サーバーはエラーを生成します。  
  
 **IgnoreAll**  
 サーバーは、MDX スクリプト内のエラー (構文エラー、名前の解決エラーなど) を含むすべてのコマンドを無視します。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  

