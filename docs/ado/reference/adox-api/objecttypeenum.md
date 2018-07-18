---
title: ObjectTypeEnum |Microsoft ドキュメント
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
- ObjectTypeEnum
helpviewer_keywords:
- ObjectTypeEnum enumeration [ADOX]
ms.assetid: 3fdecfca-aa91-4596-ad98-610f1b7f840b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4c9cb6239cee3bd6416e587dc77d55e287da68e4
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35286761"
---
# <a name="objecttypeenum"></a>ObjectTypeEnum
Ownership のいずれかのアクセス許可を設定する対象のデータベース オブジェクトの種類を指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adPermObjColumn**|2|オブジェクトは、列です。|  
|**adPermObjDatabase**|3|オブジェクトは、データベースです。|  
|**adPermObjProcedure**|4|オブジェクトは、プロシージャです。|  
|**adPermObjProviderSpecific**|-1|オブジェクトは、プロバイダーによって定義された型です。 場合、エラーが発生、 *ObjectType*パラメーターは**adPermObjProviderSpecific**と*ObjectTypeId*が指定されていません。|  
|**adPermObjTable**|1|オブジェクトは、テーブルです。|  
|**adPermObjView**|5|オブジェクトは、ビューです。|  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[GetObjectOwner メソッド (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)|[GetPermissions メソッド (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)|  
|[SetObjectOwner メソッド](../../../ado/reference/adox-api/setobjectowner-method.md)|[SetPermissions メソッド (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)|
