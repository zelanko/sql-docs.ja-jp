---
title: getTimestamp メソッド (int, java.util.Calendar) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getTimestamp (int, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 161c559a-8651-44ba-a914-15eb6a612417
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3a86f7c3b9483257a38095adfff6969c04d43fb4
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927351"
---
# <a name="gettimestamp-method-int-javautilcalendar"></a>getTimestamp (int, java.util.Calendar) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  パラメーターに渡されたインデックスと Calendar オブジェクトを使用して、指定されたパラメーターの値を Java プログラミング言語の java.sql.Timestamp オブジェクトとして取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Timestamp getTimestamp(int index,  
                                       java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *インデックス*  
  
 パラメーターのインデックスを示す **int** です。  
  
 *cal*  
  
 Calendar オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 Timestamp オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getTimestamp メソッドは、java.sql.CallableStatement インターフェイスの getTimestamp メソッドで規定されています。  
  
 このメソッドでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の **datetime** 列と **smalldatetime** 列からのみ値が返されます。  
  
## <a name="see-also"></a>参照  
 [getTimestamp メソッド &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/gettimestamp-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
