---
title: updateDateTimeOffset(int) (SQLServerResultSet) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 21ec0054-c808-4e88-9c8d-c71b696ce658
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c5a216a94ffa49015684bc349e460bf758ac1666
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47749752"
---
# <a name="updatedatetimeoffsetint-microsoftsqldatetimeoffset-sqlserverresultset"></a>updateDateTimeOffset(int, microsoft.sql.DateTimeOffset) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  このメソッドは [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 で追加されました。  
  
 0 から始まる列の序数を使用して、指定された列の値を [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)値に更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateDateTimeOffset(int index, microsoft.sql.DateTimeOffset x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *index*  
  
 列の 0 から始まる序数です。  
  
 *x*  
  
 A [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 取得することができます、 [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)値と[SQLServerResultSet.getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)します。  
  
## <a name="see-also"></a>参照  
 [updateDateTimeOffset &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatedatetimeoffset-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
