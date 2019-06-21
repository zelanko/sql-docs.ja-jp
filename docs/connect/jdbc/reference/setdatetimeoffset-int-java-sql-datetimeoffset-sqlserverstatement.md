---
title: setDateTimeOffset(int, java.sql.DateTimeOffset) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e8b6e380-6b53-489b-be73-73fcb5258269
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 36b23fb46e8cd909cf71e696293f2981731a86d2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66793915"
---
# <a name="setdatetimeoffsetint-javasqldatetimeoffset-sqlserverstatement"></a>setDateTimeOffset(int, java.sql.DateTimeOffset) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターを、渡された DateTimeOffset 値に設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setDateTimeOffset(int parameterIndex, DateTimeOffset dateTime)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *parameterIndex*  
  
 設定する列のインデックスです。  
  
 *dateTimeOffset*  
  
 DateTimeOffset オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 DateTimeOffset の形式は "YYYY-MM-DD HH-MM-SS[.nnnnnnn] [+][-] HH:MM" です。 次の表を参照してください。  
  
|SQL 型|Insert|  
|--------------|------------|  
|DATETIME|挿入できる唯一の形式: "YYYY-MM-DD hh:mm:ss[.nnn]"|  
|smalldatetime|挿入できる唯一の形式: "YYYY-MM-DD hh:mm:ss"|  
|Time|挿入できる唯一の形式: "hh:mm:ss[.nnnnnnn]"|  
|date|挿入できる唯一の形式: "YYYY-MM-DD"|  
|datetime2|挿入できる唯一の形式: "YYYY-MM-DD hh:mm:ss[.nnnnnnn]"|  
  
## <a name="see-also"></a>参照  
 [getDateTimeOffset &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)   
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
