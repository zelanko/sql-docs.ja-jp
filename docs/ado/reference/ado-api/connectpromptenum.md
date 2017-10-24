---
title: "ConnectPromptEnum |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ConnectPromptEnum
helpviewer_keywords:
- ConnectPromptEnum enumeration [ADO]
ms.assetid: 21026e24-62b7-4cc9-8aef-62c1fc6cba75
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8ae0c2179e321e521a86fdc76e5f8978ab4ab747
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="connectpromptenum"></a>ConnectPromptEnum
データ ソースへの接続を開くときに、不足しているパラメーターを要求するダイアログ ボックスを表示するかどうかを指定します。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**される**|1|常にメッセージが表示されます。|  
|**adPromptComplete**|2|詳細については、必要な場合は、メッセージが表示されます。|  
|**adPromptCompleteRequired**|3|詳細については、必要なが省略可能なパラメーターは使用できない場合のプロンプトを表示します。|  
|**adPromptNever**|4|要求しません。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.ConnectPrompt.ALWAYS|  
|AdoEnums.ConnectPrompt.COMPLETE|  
|AdoEnums.ConnectPrompt.COMPLETEREQUIRED|  
|AdoEnums.ConnectPrompt.NEVER|  
  
## <a name="applies-to"></a>適用対象  
 [プロンプトのプロパティ-動的 (ADO)](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)

