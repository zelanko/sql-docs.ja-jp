---
title: "値の |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ParameterDirectionEnum
helpviewer_keywords:
- ParameterDirectionEnum enumeration [ADO]
ms.assetid: c66aa6e6-d4f0-4f0f-9640-e08ae6cfdef3
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c32176b7c9c5dc235c77e5f2363f1fc51ae9bb40
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="parameterdirectionenum"></a>値
指定するかどうか、[パラメーター](../../../ado/reference/ado-api/parameter-object.md)入力パラメーター、出力パラメーター両方の入力を表しますと出力パラメーター、またはストアド プロシージャからの戻り値。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adParamInput**|1|既定値です。 パラメーターが入力パラメーターを表すことを示します。|  
|**adParamInputOutput**|3|パラメーターが入力と出力の両方のパラメーターを表すことを示します。|  
|**adParamOutput**|2|パラメーターが出力パラメーターを表すことを示します。|  
|**adParamReturnValue**|4|パラメーターが戻り値を表すことを示します。|  
|**adParamUnknown**|0|パラメーターの方向が既知であることを示します。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.ParameterDirection.INPUT|  
|AdoEnums.ParameterDirection.INPUTOUTPUT|  
|AdoEnums.ParameterDirection.OUTPUT|  
|AdoEnums.ParameterDirection.RETURNVALUE|  
|AdoEnums.ParameterDirection.UNKNOWN|  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[CreateParameter メソッド (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)|[方向プロパティ](../../../ado/reference/ado-api/direction-property.md)|

