---
description: ObjectTypeEnum
title: ObjectTypeEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ObjectTypeEnum
helpviewer_keywords:
- ObjectTypeEnum enumeration [ADOX]
ms.assetid: 3fdecfca-aa91-4596-ad98-610f1b7f840b
author: rothja
ms.author: jroth
ms.openlocfilehash: 22b2c36ab87079c7bc984606a36397a98ea67af7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439754"
---
# <a name="objecttypeenum"></a>ObjectTypeEnum
権限または所有権を設定するデータベースオブジェクトの種類を指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adPermObjColumn**|2|オブジェクトは列です。|  
|**adPermObjDatabase**|3|オブジェクトはデータベースです。|  
|**adPermObjProcedure**|4|オブジェクトはプロシージャです。|  
|**adPermObjProviderSpecific**|-1|オブジェクトは、プロバイダーによって定義された型です。 *ObjectType*パラメーターが**Adpermobjproviderspecific**で*objecttypeid*が指定されていない場合、エラーが発生します。|  
|**adPermObjTable**|1|オブジェクトはテーブルです。|  
|**adPermObjView**|5|オブジェクトはビューです。|  
  
## <a name="applies-to"></a>適用対象  

:::row:::
    :::column:::
        [GetObjectOwner メソッド (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)  
        [GetPermissions メソッド (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)  
    :::column-end:::
    :::column:::
        [SetObjectOwner メソッド](../../../ado/reference/adox-api/setobjectowner-method.md)  
        [SetPermissions メソッド (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)  
    :::column-end:::
:::row-end:::
