---
title: SynchronizeSecurity 要素 (XMLA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- SynchronizeSecurity Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.synchronizesecurity
- http://schemas.microsoft.com/analysisservices/2003/engine#SynchronizeSecurity
- urn:schemas-microsoft-com:xml-analysis#SynchronizeSecurity
helpviewer_keywords:
- SynchronizeSecurity element
ms.assetid: d37dbb95-f4a4-44ac-8eb9-f661d5bb5018
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: cc50a9acd38fe394e5ac6b457f72e76669b5ec64
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073087"
---
# <a name="synchronizesecurity-element-xmla"></a>SynchronizeSecurity 要素 (XMLA)
  中に、ロールや権限などのセキュリティ定義を同期する方法を指定、[同期](../xml-elements-commands/synchronize-element-xmla.md)コマンド。  
  
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
|親要素|[同期](../xml-elements-commands/synchronize-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Security` 要素は、ロールや権限など、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベースで定義されているセキュリティ定義を、`Synchronize` コマンドの実行時に同期するかどうかを決定します。 この要素は、セキュリティ定義のメンバーとして定義された Windows ユーザー アカウントとグループを `Synchronize` コマンドに含めるかどうかも決定します。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*SkipMembership*|`Synchronize` コマンドの実行時にセキュリティ定義を含めますが、メンバーシップ情報は除外します。|  
|*CopyAll*|`Synchronize` コマンドの実行時にセキュリティ定義およびメンバーシップ情報を含めます。|  
|*IgnoreSecurity*|`Synchronize` コマンドの実行時にセキュリティ定義を除外します。|  
  
## <a name="see-also"></a>参照  
 [セキュリティ要素&#40;XMLA&#41;](security-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  