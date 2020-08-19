---
description: ConnectPromptEnum
title: ConnectPromptEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ConnectPromptEnum
helpviewer_keywords:
- ConnectPromptEnum enumeration [ADO]
ms.assetid: 21026e24-62b7-4cc9-8aef-62c1fc6cba75
author: rothja
ms.author: jroth
ms.openlocfilehash: 0ad8fe77bb3472931d3b16d5849b047001922c96
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444414"
---
# <a name="connectpromptenum"></a>ConnectPromptEnum
データソースへの接続を開くときにダイアログボックスを表示して、不足しているパラメーターを確認するかどうかを指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adPromptAlways**|1|常にプロンプトを表示します。|  
|**adPromptComplete**|2|詳細情報が必要かどうかを確認するメッセージが表示されます。|  
|**adPromptCompleteRequired**|3|詳細情報が必要かどうかを確認するメッセージが表示されますが、省略可能なパラメーターは使用できません。|  
|**adPromptNever**|4|プロンプトが表示されません。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|定数|  
|--------------|  
|AdoEnums を常に確認します。|  
|AdoEnums を実行します。|  
|AdoEnums COMPLETEREQUIRED|  
|AdoEnums。 NEVER|  
  
## <a name="applies-to"></a>適用対象  
 [Prompt プロパティ - 動的 (ADO)](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)
