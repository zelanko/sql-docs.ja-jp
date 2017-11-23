---
title: "SynchronizeSecurity 要素 (XMLA) |Microsoft ドキュメント"
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
apiname: SynchronizeSecurity Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.synchronizesecurity
- http://schemas.microsoft.com/analysisservices/2003/engine#SynchronizeSecurity
- urn:schemas-microsoft-com:xml-analysis#SynchronizeSecurity
helpviewer_keywords: SynchronizeSecurity element
ms.assetid: d37dbb95-f4a4-44ac-8eb9-f661d5bb5018
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 34ec0a8e5573bbdc33b8aca1f1338c20b9f93099
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="synchronizesecurity-element-xmla"></a>SynchronizeSecurity 要素 (XMLA)
  中に、ロールや権限などのセキュリティ定義を同期する方法を指定、[同期](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)コマンド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Synchronize>  
   ...  
   <SynchronizeSecurity>...</SynchronizeSecurity>  
   ...  
</Synchronize>  
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
|親要素|[同期](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **セキュリティ**要素は、ロールや権限など、セキュリティ定義で定義されているかどうかを決定する[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]中にデータベースが同期されている、**同期**コマンド。 この要素が Windows ユーザー アカウントと、セキュリティ定義のメンバーとして定義されているグループがの一部として含まれるかどうかを決定しても、**同期**コマンド。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*SkipMembership*|セキュリティの定義が含まれますが、中に、メンバーシップ情報を除外する**同期**コマンド。|  
|*CopyAll*|セキュリティの定義と中にメンバーシップ情報が含まれて、**同期**コマンド。|  
|*Ignoresecurity のいずれか*|実行時にセキュリティ定義を除外する、**同期**コマンド。|  
  
## <a name="see-also"></a>参照  
 [セキュリティ要素 &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/security-element-xmla.md)   
 [プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
