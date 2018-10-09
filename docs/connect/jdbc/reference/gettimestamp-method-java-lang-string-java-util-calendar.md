---
title: getTimestamp (java.lang.String, java.util.Calendar) メソッド | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getTimestamp (java.lang.String,java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 770668d9-2e52-4ff0-be2f-ebf78fd41644
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 27ee52e2dd8acb976d732baa76d32a0401ba445d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47666090"
---
# <a name="gettimestamp-method-javalangstring-javautilcalendar"></a>getTimestamp (java.lang.String, java.util.Calendar) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  パラメーターに渡された名前と Calendar オブジェクトを使用して、指定されたパラメーターの値が Java プログラミング言語の java.sql.Timestamp オブジェクトとして取得されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Timestamp getTimestamp(java.lang.String name,  
                                       java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *name*  
  
 パラメーターの名前を含む**文字列**です。  
  
 *cal*  
  
 暦オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 タイムスタンプのオブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getTime メソッドは、java.sql.CallableStatement インターフェイスの getTime メソッドで規定されています。  
  
 このメソッドでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の **datetime** 列と **smalldatetime** 列からのみ値が返されます。  
  
## <a name="see-also"></a>参照  
 [getTimestamp メソッド &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/gettimestamp-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
