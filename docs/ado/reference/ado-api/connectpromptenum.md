---
title: ConnectPromptEnum |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
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
ms.openlocfilehash: 62b1bb38789dcfb2fd15b80501315d9c1be38a66
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277241"
---
# <a name="connectpromptenum"></a>ConnectPromptEnum
データ ソースへの接続を開くときに、不足しているパラメーターを要求するダイアログ ボックスを表示するかどうかを指定します。  
  
|定数|値|説明|  
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
