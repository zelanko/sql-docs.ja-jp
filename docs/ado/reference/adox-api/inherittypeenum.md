---
title: InheritTypeEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- InheritTypeEnum
helpviewer_keywords:
- InheritTypeEnum enumeration [ADOX]
ms.assetid: c2f6ce79-c4b3-4d40-ac95-21025208f991
author: MightyPen
ms.author: genemi
ms.openlocfilehash: aef8f768dd991e4e6ed740cc56600a6f1a8020e0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67965950"
---
# <a name="inherittypeenum"></a>InheritTypeEnum
[SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md)で設定された権限をオブジェクトが継承する方法を指定します。  
  
|Constant|値|説明|  
|--------------|-----------|-----------------|  
|**adInheritBoth**|3|オブジェクトと、プライマリオブジェクトに含まれるその他のコンテナーは両方ともエントリを継承します。|  
|**adInheritContainers**|2|プライマリオブジェクトに含まれる他のコンテナーは、エントリを継承します。|  
|**adInheritNone**|0|既定値。 継承は行われません。|  
|**adInheritNoPropagate**|4|**Adinheritobjects**と**adinheritobjects**フラグは、継承されたエントリには反映されません。|  
|**adInheritObjects**|1|コンテナー内のコンテナー以外のオブジェクトは、アクセス許可を継承します。|  
  
## <a name="applies-to"></a>適用対象  
 [SetPermissions メソッド (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
