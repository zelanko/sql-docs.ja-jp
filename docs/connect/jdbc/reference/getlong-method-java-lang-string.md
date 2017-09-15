---
title: "getLong (java.lang.String) メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerCallableStatement.getLong (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 92e30537-5fd9-4b67-8b0f-486c6e840e03
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f3caf7b3418ebfb042f5a774da137d820a43cb6a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getlong-method-javalangstring"></a>getLong (java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  として指定されたパラメーターの値を取得、**長い**java プログラミング言語のパラメーター名を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public long getLong(java.lang.String sCol)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sCol*  
  
 A**文字列**パラメーター名を格納しています。  
  
## <a name="return-value"></a>戻り値  
 A**長い**値。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getLong メソッドは、java.sql.CallableStatement インターフェイスの getLong メソッドによって指定されます。  
  
 このメソッドでのみサポートされて[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]できますを安全に返す整数値などのデータ型**bigint**、 **int**、 **smallint**、 **tinyint**、および**ビット**です。 このメソッドを他のデータ型で使用すると、例外がスローされます。  
  
## <a name="see-also"></a>参照  
 [getLong メソッド & #40 です。SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getlong-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
