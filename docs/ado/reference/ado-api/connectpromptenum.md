---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: afd5d9ca0de6b8d2ffba75f862e6ca0afb594848
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67919445"
---
# <a name="connectpromptenum"></a>ConnectPromptEnum
データソースへの接続を開くときにダイアログボックスを表示して、不足しているパラメーターを確認するかどうかを指定します。  
  
|Constant|[値]|説明|  
|--------------|-----------|-----------------|  
|**adPromptAlways**|1|常にプロンプトを表示します。|  
|**adPromptComplete**|2|詳細情報が必要かどうかを確認するメッセージが表示されます。|  
|**adPromptCompleteRequired**|3|詳細情報が必要かどうかを確認するメッセージが表示されますが、省略可能なパラメーターは使用できません。|  
|**adPromptNever**|4|プロンプトが表示されません。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|Constant|  
|--------------|  
|AdoEnums を常に確認します。|  
|AdoEnums を実行します。|  
|AdoEnums COMPLETEREQUIRED|  
|AdoEnums。 NEVER|  
  
## <a name="applies-to"></a>適用対象  
 [Prompt プロパティ - 動的 (ADO)](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)
