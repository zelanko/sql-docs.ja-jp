---
title: "getColumnLabel メソッド (SQLServerResultSetMetaData) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerResultSetMetaData.getColumnLabel
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: cf67692c-24aa-49e6-8e88-a47d4e8c021c
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e1ba263019455a8e6c439fdb69d46da2e0443a34
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getcolumnlabel-method-sqlserverresultsetmetadata"></a>getColumnLabel メソッド (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列の印刷や表示に使用する推奨タイトルを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getColumnLabel(int column)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *列*  
  
 **Int**列インデックスを示すです。  
  
## <a name="return-value"></a>戻り値  
 A**文字列**列のタイトルを格納しています。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getColumnLabel メソッドは、java.sql.ResultSetMetaData インターフェイスの getColumnLabel メソッドによって指定されます。  
  
 このメソッドは、列の別名を返します。 別名が使用できない場合は列名を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSetMetaData のメソッド](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData のメンバー](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData クラス](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
