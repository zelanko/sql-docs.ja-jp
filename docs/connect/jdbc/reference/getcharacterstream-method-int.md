---
title: "getCharacterStream (int) メソッド |Microsoft ドキュメント"
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
apiname: SQLServerResultSet.getCharacterStream (int)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 4f9f230d-be4c-469a-b3dc-f24531429aae
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f345dc0fe0c52b4c70d280fbbd6c893095dbf36c
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getcharacterstream-method-int"></a>getCharacterStream (int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この現在の行に指定された列インデックスの値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトを java.io.Reader オブジェクトとして。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.io.Reader getCharacterStream(int columnIndex)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnIndex*  
  
 **Int**列インデックスを示すです。  
  
## <a name="return-value"></a>戻り値  
 リーダー オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getCharacterStream メソッドは、java.sql.ResultSet インターフェイスの getCharacterStream メソッドによって指定されます。  
  
 このメソッドは読み取り専用[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]nchar、nvarchar、nvarchar (max)、および ntext などの Unicode 文字データ型。 ASCII 文字型などのその他のデータ型では、例外がスローされます。 ASCII データ型を読み取り、使用、 [getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlserverresultset.md)メソッドです。  
  
## <a name="see-also"></a>参照  
 [getCharacterStream メソッド &#40;です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
