---
title: "Banner 要素 (ssbdiagnose) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- banner element
- XML output file format [ssbdiagnose], banner element
- ssbdiagnose
ms.assetid: cc6cd49a-acf0-4cfb-8c6a-554692b89de2
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0b203f5c2f9700137409df074935c2f17daf08d7
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="banner-element-ssbdiagnose"></a>Banner 要素 (ssbdiagnose)
  **ssbdiagnose** の出力 XML ファイルを生成したユーティリティを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Banner  
    title="..."   
    product="..."   
    version="..." />  
```  
  
## <a name="element-attributes"></a>要素の属性  
  
|属性|説明|  
|---------------|-----------------|  
|**title**|**ssbdiagnose** の XML 出力ファイルを生成したユーティリティを示します。|  
|**product**|**ssbdiagnose** の XML 出力ファイルを生成した製品を示します。|  
|**version**|XML 出力ファイルを生成したユーティリティのバージョンを示します。|  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|**ssbdiagnose** の出力 XML ファイルにつき 1 個。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[DiagnosticInformation 要素 & #40";"ssbdiagnose"&"#41;](../../tools/ssbdiagnose/diagnosticinformation-element-ssbdiagnose.md)|  
|**子要素**|[なし] :|  
  
## <a name="example"></a>例  
 バナー要素の例を次に示します。  
  
```  
<Banner title="Service Broker Diagnostics Utility" product="Microsoft SQL Server" version="10.0.1073.0" />  
```  
  
## <a name="see-also"></a>参照  
 [ssbdiagnose ユーティリティ & #40 です。Service Broker &#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  

