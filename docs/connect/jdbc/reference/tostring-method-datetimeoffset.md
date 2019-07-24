---
title: toString メソッド (DateTimeOffset) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e77b9be3-1a02-4769-8acf-ac71d48d6a76
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ef3cd31068c324475e8edfe8bf8f7c16acc4a2de
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67968511"
---
# <a name="tostring-method-datetimeoffset"></a>toString (DateTimeOffset) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  **DateTimeOffset**オブジェクトの文字列表現を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public String toString()  
```  
  
## <a name="return-value"></a>戻り値  
 **DateTimeOffset**オブジェクトの文字列表現。  
  
## <a name="remarks"></a>Remarks  
 文字列の形式は*YYYY*-*MM*-*DD * * hh*:*MM*:*ss*[です。*fffffff*] [+ |-]*hh*:*mm*。  
  
 返される文字列の小数部では、宣言されている有効桁数になるまでゼロが埋め込まれます。 たとえば、値が "2010-03-10 12:34: 56.78-08:00" の**datetimeoffset (6)** は、datetimeoffset によって "2010-03-10 12:34: 56.780000-08:00" として書式設定されます。  
  
## <a name="see-also"></a>参照  
 [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset のメンバー](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
