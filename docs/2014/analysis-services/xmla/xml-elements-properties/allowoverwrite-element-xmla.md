---
title: AllowOverwrite 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AllowOverwrite Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.allowoverwrite
- urn:schemas-microsoft-com:xml-analysis#EndSession
helpviewer_keywords:
- AllowOverwrite element
ms.assetid: e7e92481-5f29-47f2-9efd-4e5e60c002bb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: eb0d58570349fbbb17b442ddebc0fd3193531149
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48131432"
---
# <a name="allowoverwrite-element-xmla"></a>AllowOverwrite 要素 (XMLA)
  決定かどうか、親[バックアップ](../xml-elements-commands/backup-element-xmla.md)または[復元](../xml-elements-commands/restore-element-xmla.md)コマンドは、ターゲット ファイルまたはデータベースを上書きしようとしています。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <AllowOverwrite>...</AllowOverwrite>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|False|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[バックアップ](../xml-elements-commands/backup-element-xmla.md)、[復元](../xml-elements-commands/restore-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Backup` コマンドの場合、`AllowOverwrite` 要素は、`File` 要素で指定されたバックアップ ファイルをコマンドが上書きできるかどうかを決定します。  
  
 `Restore` 、要素、`AllowOverwrite`要素は、コマンドが上書きできるかどうかを決定、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]で指定されたデータベース、`DatabaseName`要素。  
  
## <a name="see-also"></a>参照  
 [DatabaseName 要素&#40;XMLA&#41;](name-element-xmla.md)   
 [要素が&#40;XMLA&#41;](file-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
