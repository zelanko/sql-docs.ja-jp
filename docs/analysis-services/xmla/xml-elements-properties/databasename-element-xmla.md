---
title: "DatabaseName 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DatabaseName Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.databasename
- http://schemas.microsoft.com/analysisservices/2003/engine#DatabaseName
- urn:schemas-microsoft-com:xml-analysis#DatabaseName
helpviewer_keywords:
- DatabaseName element
ms.assetid: 5cfd9a1f-da53-497a-b677-c51be4641bd0
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 999ffdf13c208c7bfd67118d1c692b1c1f70cf3b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="databasename-element-xmla"></a>DatabaseName 要素 (XMLA)
  識別、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]親を復元するデータベース[復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)コマンド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Restore>  
   ...  
   <DatabaseName>...</DatabaseName>  
   ...  
</Restore>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[復元]](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **DatabaseName**要素は、先のデータベースを識別、**復元**コマンドは、バックアップ ファイルを復元します。 この要素が指定されない場合、あるいは空の文字列が含まれる場合には、バックアップ ファイル内に含まれるデータベースの名前が使用されます。  
  
 対象のインスタンスにデータベースが既に存在するエラーが発生しない限り、 **AllowOverwrite**親要素**復元**コマンドに設定されている**True**です。  
  
## <a name="see-also"></a>参照  
 [AllowOverwrite 要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md)   
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

