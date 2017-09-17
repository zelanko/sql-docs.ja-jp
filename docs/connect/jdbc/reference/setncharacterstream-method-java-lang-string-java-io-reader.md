---
title: "setNCharacterStream メソッドをリーダー オブジェクトの文字列 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd19fbb8-a878-4d98-a584-e4969d649844
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 51250ced4a6925bba1493346f48ddc6035b20005
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setncharacterstream-method-javalangstring-javaioreader"></a>setNCharacterStream (java.lang.String, java.io.Reader) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された Reader オブジェクトを指定されたパラメーターを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setNCharacterStream(java.lang.String parameterName,  
                       java.io.Reader value)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *パラメーター名*  
  
 A**文字列**パラメーターの名前を示すです。  
  
 *value*  
  
 リーダー オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setNCharacterStream メソッドは、java.sql.CallableStatement インターフェイスの setNCharacterStream メソッドによって指定されます。  
  
 このメソッドを使用する必要があります**NCHAR**、 **NVARCHAR**、 **NTEXT**、および**XML**データ型。  
  
## <a name="see-also"></a>参照  
 [setNCharacterStream メソッド & #40 です。SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/setncharacterstream-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
