---
title: getLong (java.lang.String) メソッド (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 546d77e2-723a-42ac-ba3f-fabf2395d376
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2fc3df07bcdb342b5796b6472d7e8b96ba1674b9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47826990"
---
# <a name="getnstring-method-javalangstring-sqlserverresultset"></a>getNString (java.lang.String) メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトの現在の行にある指定された列の値が、SQLXML オブジェクトとして取得されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getNString(java.lang.String columnLabel)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnLabel*  
  
 列ラベルを含む文字列です。  
  
## <a name="return-value"></a>戻り値  
 文字列オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getNString メソッドは、java.sql.SQLServerResultSet インターフェイスで getNString メソッドによって指定されます。  
  
 値を取得するこのメソッドを使用できます、 **nvarchar**、 **nchar**、 **nvarchar (max)**、 **ntext**、または**xml**これの現在の行に列[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。 このメソッドを使用して他のデータ型の値を取得しようとすると、例外がスローされます。  
  
## <a name="see-also"></a>参照  
 [getString メソッド &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getnstring-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)  
  
  
