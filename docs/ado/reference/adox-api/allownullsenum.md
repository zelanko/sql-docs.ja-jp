---
description: AllowNullsEnum
title: AllowNullsEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- AllowNullsEnum
helpviewer_keywords:
- AllowNullsEnum enumeration [ADOX]
ms.assetid: 6acf3689-1a7f-4379-9d7f-df452ccbac27
author: rothja
ms.author: jroth
ms.openlocfilehash: 058df53811bfbb48005f1f9c6f08f38410bc54cf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440504"
---
# <a name="allownullsenum"></a>AllowNullsEnum
Null 値を持つレコードのインデックスを作成するかどうかを指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adIndexNullsAllow**|0|インデックスでは、キー列が null であるエントリが許可されます。 キー列に null 値を入力すると、エントリがインデックスに挿入されます。|  
|**adIndexNullsDisallow**|1|既定値。 インデックスでは、キー列が null であるエントリは許可されません。 キー列に null 値が入力されると、エラーが発生します。|  
|**adIndexNullsIgnore**|2|インデックスでは、null キーを含むエントリは挿入されません。 キー列に null 値を入力した場合、エントリは無視され、エラーは発生しません。|  
|**adIndexNullsIgnoreAny**|4|インデックスでは、一部のキー列が null 値を持つエントリは挿入されません。 複数列のキーを持つインデックスの場合、ある列に null 値を入力すると、エントリは無視され、エラーは発生しません。|  
  
## <a name="applies-to"></a>適用対象  
 [IndexNulls プロパティ (ADOX)](../../../ado/reference/adox-api/indexnulls-property-adox.md)
