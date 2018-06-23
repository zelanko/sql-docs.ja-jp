---
title: Password 要素 (XMLA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Password Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Password
- urn:schemas-microsoft-com:xml-analysis#Password
- microsoft.xml.analysis.password
helpviewer_keywords:
- Password element
ms.assetid: 8a0603bd-f6a1-4b86-84f1-c83d0b03951b
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: cfc62de4ad73888fb95fe179efd0fdaeabbc9dc9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085076"
---
# <a name="password-element-xmla"></a>Password 要素 (XMLA)
  親によって使用されるパスワードを決定[バックアップ](../xml-elements-commands/backup-element-xmla.md)または[復元](../xml-elements-commands/restore-element-xmla.md)コマンドの暗号化またはバックアップ ファイルを復号化します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <Password>...</Password>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[バックアップ](../xml-elements-commands/backup-element-xmla.md)、[復元](../xml-elements-commands/restore-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Backup` コマンドの場合、`Password` 要素が含まれていない、または要素の文字列が空になっていると、バックアップ ファイルは暗号化されません。  
  
 `Restore` コマンドの場合、暗号化されたバックアップ ファイルを復元するときに `Password` 要素が含まれていない、または要素の文字列が空になっていると、エラーが発生します。  
  
 `Location` 要素が `Backup` コマンドまたは `Restore` コマンドに含まれている場合、バックアップ ファイルとリモート バックアップ ファイルの両方で同じ `Password` 要素が使用されます。 リモート バックアップ ファイルの詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期&#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)です。  
  
## <a name="see-also"></a>参照  
 [Location 要素&#40;XMLA&#41;](location-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  