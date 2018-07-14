---
title: エラー処理 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- scripts [MDX], exceptions
- exceptions [MDX]
ms.assetid: bc6ff0af-9fe6-44d6-bc3c-801d71ea41a9
caps.latest.revision: 26
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bbbe021cbb65803f79a4aa0a92791441e22e9cb6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37332682"
---
# <a name="error-handling-mdx"></a>エラー処理 (MDX)
  各キューブでは、多次元式 (MDX) スクリプト内のエラーの処理方法を制御できます。 エラー処理を行う、`ScriptErrorHandlingMode`列挙子。 この列挙子は、以下のいずれかの値をとります。  
  
 `IgnoreNone`  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] が MDX スクリプト内になんらかのエラーを検出した場合、サーバーはエラーを生成します。  
  
 `IgnoreAll`  
 サーバーは、MDX スクリプト内のエラー (構文エラー、名前の解決エラーなど) を含むすべてのコマンドを無視します。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  
