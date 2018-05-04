---
title: ConnectPromptEnum |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ConnectPromptEnum
helpviewer_keywords:
- ConnectPromptEnum enumeration [ADO]
ms.assetid: 21026e24-62b7-4cc9-8aef-62c1fc6cba75
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b8f01de20cabf1ec5d7cefdb645fb1fc08b69d31
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="connectpromptenum"></a>ConnectPromptEnum
データ ソースへの接続を開くときに、不足しているパラメーターを要求するダイアログ ボックスを表示するかどうかを指定します。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adPromptAlways**|1|常にメッセージが表示されます。|  
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
 [Prompt プロパティ - 動的 (ADO)](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)
