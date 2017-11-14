---
title: "セキュリティ要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Security Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.security
- urn:schemas-microsoft-com:xml-analysis#Security
- http://schemas.microsoft.com/analysisservices/2003/engine#Security
helpviewer_keywords:
- Security element
ms.assetid: 0b601f69-d16d-4d10-9361-b8afaa6ed357
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: cd1a4c292c1ac722fd91836b364724a0f59f8168
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="security-element-xmla"></a>Security 要素 (XMLA)
  バックアップまたは中に、ロールや権限などのセキュリティ定義を復元する方法を指定、[バックアップ](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)または[復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)コマンド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <Security>...</Security>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*SkipMembership*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[バックアップ](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)、[復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **セキュリティ**要素は、ロールや権限など、セキュリティ定義で定義されているかどうかを決定する[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベースのバックアップまたは復元中に、それぞれ、**バックアップ**または**復元**コマンド。 この要素が Windows ユーザー アカウントと、セキュリティ定義のメンバーとして定義されているグループがの一部として含まれるかどうかを決定しても、**バックアップ**または**復元**コマンド。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*SkipMembership*|セキュリティの定義が含まれますが、中に、メンバーシップ情報を除外**バックアップ**または**復元**コマンド。|  
|*CopyAll*|セキュリティ定義とメンバーシップ情報中に含めます**バックアップ**または**復元**コマンド。|  
|*Ignoresecurity のいずれか*|実行時にセキュリティ定義を除外する**バックアップ**または**復元**コマンド。|  
  
## <a name="see-also"></a>参照  
 [SynchronizeSecurity 要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/synchronizesecurity-element-xmla.md)   
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

