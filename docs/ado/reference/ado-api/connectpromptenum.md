---
title: "ConnectPromptEnum |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: ConnectPromptEnum
helpviewer_keywords: ConnectPromptEnum enumeration [ADO]
ms.assetid: 21026e24-62b7-4cc9-8aef-62c1fc6cba75
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 89c339b294a3afc968a6a9f5307d3a06995a7454
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="connectpromptenum"></a>ConnectPromptEnum
データ ソースへの接続を開くときに、不足しているパラメーターを要求するダイアログ ボックスを表示するかどうかを指定します。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**される**|@shouldalert|常にメッセージが表示されます。|  
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
