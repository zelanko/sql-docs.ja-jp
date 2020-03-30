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
ms.openlocfilehash: 166c9ddbd4b5c11b3c032a5a4ecf43c95f183473
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "67974533"
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
  
|SQL 型|挿入|  
|--------------|------------|  
|DATETIME|挿入できる唯一の形式: "YYYY-MM-DD hh:mm:ss[.nnn]"|  
|smalldatetime|挿入できる唯一の形式: "YYYY-MM-DD hh:mm:ss"|  
|Time|挿入できる唯一の形式: "hh:mm:ss[.nnnnnnn]"|  
|Date|挿入できる唯一の形式: "YYYY-MM-DD"|  
|DateTime2|挿入できる唯一の形式: "YYYY-MM-DD hh:mm:ss[.nnnnnnn]"|  
  
## <a name="see-also"></a>参照  
 [getDateTimeOffset &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)   
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
