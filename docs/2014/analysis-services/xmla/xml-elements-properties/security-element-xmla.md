---
title: Security 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Security Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.security
- urn:schemas-microsoft-com:xml-analysis#Security
- http://schemas.microsoft.com/analysisservices/2003/engine#Security
helpviewer_keywords:
- Security element
ms.assetid: 0b601f69-d16d-4d10-9361-b8afaa6ed357
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 784a3f6b56c0372897b984c5fac4e8915cb53ebc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48111970"
---
# <a name="security-element-xmla"></a>Security 要素 (XMLA)
  バックアップまたは中に、ロールや権限などのセキュリティ定義を復元する方法を指定します、[バックアップ](../xml-elements-commands/backup-element-xmla.md)または[復元](../xml-elements-commands/restore-element-xmla.md)コマンド。  
  
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
|既定値|*skipMembership*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[バックアップ](../xml-elements-commands/backup-element-xmla.md)、[復元](../xml-elements-commands/restore-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Security` 要素は、`Backup` または `Restore` コマンドの実行時に、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベースに対して定義されているセキュリティ定義 (ロール、権限など) をバックアップまたは復元するかどうかを決定します。 この要素は、セキュリティ定義のメンバーとして定義された Windows ユーザー アカウントとグループを、`Backup` または `Restore` コマンドに含めるかどうかも決定します。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*skipMembership*|`Backup` または `Restore` コマンドの実行時にセキュリティ定義を含めますが、メンバーシップ情報は除外します。|  
|*CopyAll*|`Backup` または `Restore` コマンドの実行時に、セキュリティ定義およびメンバーシップ情報を含めます。|  
|*IgnoreSecurity*|`Backup` または `Restore` コマンドの実行時にセキュリティ定義を除外します。|  
  
## <a name="see-also"></a>参照  
 [SynchronizeSecurity 要素&#40;XMLA&#41;](security-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
