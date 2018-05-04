---
title: NamedParameters プロパティ (ADO) |Microsoft ドキュメント
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
- _Command::NamedParameters
helpviewer_keywords:
- NamedParameters property [ADO]
ms.assetid: 42409387-026c-435f-a9b1-bf4167095875
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 37ae6f8714e555698f2627f83a8629073738b0e5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="namedparameters-property-ado"></a>NamedParameters プロパティ (ADO)
パラメーター名をプロバイダーに渡す必要があるかどうかを示します。  
  
## <a name="remarks"></a>解説  
 ADO がの値を渡しますこのプロパティが true の場合、**名前**内の各パラメーターのプロパティ、**パラメーター**のコレクション、[コマンド オブジェクト](../../../ado/reference/ado-api/command-object-ado.md)です。 プロバイダーでパラメーターに一致するパラメーター名を使用して、 **CommandText**または**CommandStream**プロパティです。 このプロパティが false の場合 (既定値) は、パラメーター名は無視され、プロバイダーでは、パラメーターの順序を使用して、パラメーターに値を照合する、 **CommandText**または**CommandStream**プロパティです。  
  
## <a name="applies-to"></a>適用対象  
 [Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [CommandText プロパティ (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [CommandStream プロパティ (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md)   
 [Parameters コレクション (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
