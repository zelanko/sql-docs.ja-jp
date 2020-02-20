---
title: getTimestamp メソッド (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getTimestamp (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4d5174db-365c-4476-9472-7871578ef34c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 999cfba0f0bd98bfc7e13f436303160ef66962b3
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67978736"
---
# <a name="gettimestamp-method-javalangstring"></a>getTimestamp (java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  パラメーターに渡された名前を使用して、指定されたパラメーターの値を Java プログラミング言語の java.sql.Timestamp オブジェクトとして取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Timestamp getTimestamp(java.lang.String sCol)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sCol*  
  
 パラメーターの名前を含む**文字列**です。  
  
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
  
  
