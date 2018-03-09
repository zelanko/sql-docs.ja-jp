---
title: "エラー処理 (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scripts [MDX], exceptions
- exceptions [MDX]
ms.assetid: bc6ff0af-9fe6-44d6-bc3c-801d71ea41a9
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f612a88976890a95b8fbd3d28826685d0e4ef414
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="error-handling-mdx"></a>エラー処理 (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
各キューブでは、多次元式 (MDX) スクリプト内のエラーの処理方法を制御できます。 エラー処理は、 **ScriptErrorHandlingMode** 列挙子を通して実行されます。 この列挙子は、以下のいずれかの値をとります。  
  
 **IgnoreNone**  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] が MDX スクリプト内になんらかのエラーを検出した場合、サーバーはエラーを生成します。  
  
 **IgnoreAll**  
 サーバーは、MDX スクリプト内のエラー (構文エラー、名前の解決エラーなど) を含むすべてのコマンドを無視します。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  
