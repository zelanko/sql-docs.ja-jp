---
title: "getNCharacterStream (java.lang.String) メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45d2695b-0727-419d-8921-a51d6feef0aa
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 58012af7ac3fe73f07cefc7a65fc97f89a858dc0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getncharacterstream-method-javalangstring"></a>getNCharacterStream (java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  パラメーター名を指定されたリーダー オブジェクトとして指定されたパラメーターの値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final java.io.Reader getNCharacterStream(java.lang.String columnLabel)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnLabel*  
  
 A**文字列**列ラベルを格納しています。  
  
## <a name="return-value"></a>戻り値  
 AReaderobject です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 アクセスする場合は、このメソッドを使用する必要があります**NCHAR**、 **NVARCHAR**と**LONGNVARCHAR**パラメーター。  
  
 この getNCharacterStream メソッドは、java.sql.CallableStatement インターフェイスの getNCharacterStream メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [getNCharacterStream メソッド & #40 です。SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getncharacterstream-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  

