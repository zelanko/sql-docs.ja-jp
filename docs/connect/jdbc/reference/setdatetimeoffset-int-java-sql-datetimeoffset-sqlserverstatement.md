---
title: "setDateTimeOffset (int, java.sql.DateTimeOffset) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8b6e380-6b53-489b-be73-73fcb5258269
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 176ae8749128565cca236817eb79bad94d839134
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

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
  
## <a name="remarks"></a>解説  
 DateTimeOffset の形式は "YYYY-MM-DD HH-MM-SS[.nnnnnnn] [+][-] HH:MM" です。 次の表を参照してください。  
  
|SQL 型|Insert|  
|--------------|------------|  
|datetime|挿入できる唯一の形式: "YYYY-MM-DD hh:mm:ss[.nnn]"|  
|smalldatetime|挿入できる唯一の形式: "YYYY-MM-DD hh:mm:ss"|  
|[時刻]|挿入できる唯一の形式: "hh:mm:ss[.nnnnnnn]"|  
|日付|挿入できる唯一の形式: "YYYY-MM-DD"|  
|datetime2|挿入できる唯一の形式: "YYYY-MM-DD hh:mm:ss[.nnnnnnn]"|  
  
## <a name="see-also"></a>参照  
 [getDateTimeOffset & #40 です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)   
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
