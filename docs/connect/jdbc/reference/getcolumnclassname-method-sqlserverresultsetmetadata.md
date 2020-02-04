---
title: getColumnClassName メソッド (SQLServerResultSetMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSetMetaData.getColumnClassName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2c118790-5dd2-4b10-93b6-7f065ee324ce
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 37c791c80c679afd70f4f1d2f3f2770fb0f38a16
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67952994"
---
# <a name="getcolumnclassname-method-sqlserverresultsetmetadata"></a>getColumnClassName メソッド (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerResultSet](../../../connect/jdbc/reference/getobject-method-sqlserverresultset.md) クラスの [getObject](../../../connect/jdbc/reference/sqlserverresultset-class.md) メソッドを呼び出して列から値を取得する場合、インスタンスが生成される Java クラスの完全修飾名を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getColumnClassName(int column)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *column*  
  
 列インデックスを示す **int** です。  
  
## <a name="return-value"></a>戻り値  
 クラスの完全修飾名を含む **String** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getColumnClassName メソッドは、java.sql.ResultSetMetaData インターフェイスの getColumnClassName メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSetMetaData メソッド](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData メンバー](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData クラス](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
