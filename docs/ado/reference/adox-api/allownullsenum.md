---
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 53fadcddd49ebf68949da0a7dca3cb37da0b5d93
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66708607"
---
# <a name="allownullsenum"></a>AllowNullsEnum
Null 値を持つレコードのインデックスを作成するかどうかを指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adIndexNullsAllow**|0|インデックス キー列が null 値のエントリを許可します。 キー列に null 値を入力すると、エントリは、インデックスに挿入されます。|  
|**adIndexNullsDisallow**|1|既定値です。 インデックスでは、エントリのキー列を null にできません。 キー列に null 値を入力すると、エラーが発生します。|  
|**adIndexNullsIgnore**|2|インデックスは、null キーが含まれるエントリを挿入できません。 キー列で null 値が入力された場合は、エントリは無視され、エラーは発生しません。|  
|**adIndexNullsIgnoreAny**|4|インデックスは、いくつかのキー列が null 値を持つエントリを挿入できません。 複数の列を持つインデックスは、いくつかの列で null 値が入力した場合は、キー、エントリは無視され、エラーは発生しません。|  
  
## <a name="applies-to"></a>適用対象  
 [IndexNulls プロパティ (ADOX)](../../../ado/reference/adox-api/indexnulls-property-adox.md)
