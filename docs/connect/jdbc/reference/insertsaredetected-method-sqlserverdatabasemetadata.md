---
title: "insertsAreDetected メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
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
apiname: SQLServerDatabaseMetaData.insertsAreDetected
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: f296cc42-9d26-48c3-a360-bcf51c31f7fb
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 46ee8da85734c79f7d7e01806387a68e8010abdf
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="insertsaredetected-method-sqlserverdatabasemetadata"></a>insertsAreDetected メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  メソッドを呼び出すことで可視の行を挿入するを検出できるかどうかを取得[rowInserted](../../../connect/jdbc/reference/rowinserted-method-sqlserverresultset.md)のメソッド、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)クラスです。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean insertsAreDetected(int type)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *型*  
  
 結果セットの種類を示す整数です。java.sql.ResultSet または SQLServerResultSet での定義に従って、次のいずれかの値を指定します。  
  
## <a name="javasqlresultset-types"></a>java.sql.ResultSet の種類  
 TYPE_FORWARD_ONLY  
  
 TYPE_SCROLL_SENSITIVE  
  
 TYPE_SCROLL_INSENSITIVE  
  
## <a name="sqlserverresultset-types"></a>SQLServerResultSet の種類  
 TYPE_SS_SCROLL_STATIC  
  
 TYPE_SS_SCROLL_KEYSET  
  
 TYPE_SS_DIRECT_FORWARD_ONLY  
  
 TYPE_SS_SERVER_CURSOR_FORWARD_ONLY  
  
 TYPE_SS_SCROLL_DYNAMIC  
  
## <a name="return-value"></a>戻り値  
 **true**行の挿入を検出できる場合は。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この insertsAreDetected メソッドは、java.sql.DatabaseMetaData インターフェイスの insertsAreDetected メソッドによって指定されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]どの種類のカーソルの挿入された行は検出されません。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
