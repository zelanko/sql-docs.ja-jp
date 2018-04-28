---
title: getNCharacterStream (int) メソッド (SQLServerResultSet) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f1cfa4e4-3e1f-4504-b0de-cc626d653661
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 58806731b46a15d07e86d95e970debec621d9b69
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getncharacterstream-method-int-sqlserverresultset"></a>getNCharacterStream (int) メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  現在の行に指定された列の値を取得、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)リーダー オブジェクトとしてオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.io.Reader getNCharacterStream(int columnIndex)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnIndex*  
  
 **Int**列インデックスを示すです。  
  
## <a name="return-value"></a>戻り値  
 リーダー オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getNCharacterStream メソッドは、getNCharacterStream、java.sql.ResultSet インターフェイスのメソッドでによって指定されます。  
  
 このメソッドは、の値を取得するために使用できます、 **nvarchar**、 **nchar**、 **nvarchar (max)**、 **ntext**、または**xml**これの現在の行に列[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。 このメソッドを使用して他のデータ型の値を取得しようとすると、例外がスローされます。  
  
## <a name="see-also"></a>参照  
 [getNCharacterStream メソッド&#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getncharacterstream-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)  
  
  
