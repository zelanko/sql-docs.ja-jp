---
title: setDateTimeOffset (int, java.sql.DateTimeOffset) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e8b6e380-6b53-489b-be73-73fcb5258269
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 722250967bca8484f359d1e33a7541d34eb3ac79
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
  
 *DateTimeOffset*  
  
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
 [getDateTimeOffset &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)   
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
