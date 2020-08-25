---
description: NamedParameters プロパティ (ADO)
title: NamedParameters プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Command::NamedParameters
helpviewer_keywords:
- NamedParameters property [ADO]
ms.assetid: 42409387-026c-435f-a9b1-bf4167095875
author: rothja
ms.author: jroth
ms.openlocfilehash: b520f60f9e08c5580e2f825a76d25c2cdcda6ae0
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774121"
---
# <a name="namedparameters-property-ado"></a>NamedParameters プロパティ (ADO)
パラメーター名をプロバイダーに渡す必要があるかどうかを示します。  
  
## <a name="remarks"></a>解説  
 このプロパティが true の場合、ADO は[コマンドオブジェクト](./command-object-ado.md)の**パラメーター**コレクション内の各パラメーターの**Name**プロパティの値を渡します。 プロバイダーは、パラメーター名を使用して、 **CommandText** または **commandstream** プロパティのパラメーターを照合します。 このプロパティが false (既定値) の場合、パラメーター名は無視され、パラメーターの順序を使用して、 **CommandText** または **commandstream** プロパティのパラメーターに値が一致します。  
  
## <a name="applies-to"></a>適用対象  
 [Command オブジェクト (ADO)](./command-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [CommandText プロパティ (ADO)](./commandtext-property-ado.md)   
 [CommandStream プロパティ (ADO)](./commandstream-property-ado.md)   
 [Parameters コレクション (ADO)](./parameters-collection-ado.md)