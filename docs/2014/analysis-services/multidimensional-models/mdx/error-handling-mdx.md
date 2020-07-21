---
title: エラー処理 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [MDX], exceptions
- exceptions [MDX]
ms.assetid: bc6ff0af-9fe6-44d6-bc3c-801d71ea41a9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 357194b9f789fdeacfb65ce3c894d4747867eafb
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546572"
---
# <a name="error-handling-mdx"></a>エラー処理 (MDX)
  各キューブでは、多次元式 (MDX) スクリプト内のエラーの処理方法を制御できます。 エラー処理は `ScriptErrorHandlingMode` 列挙子を使用して行われます。 この列挙子は、以下のいずれかの値をとります。  
  
 `IgnoreNone`  
 によって、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] MDX スクリプトでエラーが検出されると、サーバーでエラーが発生し [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ます。  
  
 `IgnoreAll`  
 サーバーは、MDX スクリプト内のエラー (構文エラー、名前の解決エラーなど) を含むすべてのコマンドを無視します。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  
