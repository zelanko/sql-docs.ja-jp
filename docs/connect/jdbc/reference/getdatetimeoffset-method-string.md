---
title: getDateTimeOffset メソッド (String) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: fedb1d75-0c3d-4eb3-ae65-da0e153265cc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f1b12914f42835c1260aefa16828713aafb25583
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47596820"
---
# <a name="getdatetimeoffset-method-string"></a>getDateTimeOffset (String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  このメソッドは [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 で追加されました。  
  
 パラメーターに渡されたインデックスを使用して、指定されたパラメーターの値が Java プログラミング言語の [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)のオブジェクトとして取得されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public microsoft.sql.DateTimeOffset getDateTimeOffset(String sCol)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sCol*  
  
 パラメーターの名前です。  
  
## <a name="return-value"></a>戻り値  
 A [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 設定することができます、 [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)のパラメーター値[SQLServerCallableStatement.setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlservercallablestatement.md)します。  
  
## <a name="see-also"></a>参照  
 [getDateTimeOffset メソッド &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
