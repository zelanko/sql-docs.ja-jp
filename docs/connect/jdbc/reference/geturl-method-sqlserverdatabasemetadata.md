---
title: getURL メソッド (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getURL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fcb66851-db5f-4ae8-b728-d129480b6f42
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f170e15ec0096d02fd98acb16e15a6ac05257f31
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779739"
---
# <a name="geturl-method-sqlserverdatabasemetadata"></a>getURL メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースの URL を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getURL()  
```  
  
## <a name="return-value"></a>戻り値  
 URL を含む**文字列**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getURL メソッドは、java.sql.DatabaseMetaData インターフェイスの getURL メソッドで規定されています。  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] を [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースと共に使用している場合、このメソッドによって次の情報を含む **String** 値が返されます。  
  
-   URL 値の "jdbc:sqlserver://"  
  
-   省略可能な接続のプロパティなど**serverName**、 **instanceName**、および**portNumber**  
  
-   ユーザーにより設定されるその他の接続プロパティと、ドライバーの既定値が空または null ではないすべての接続プロパティ (ただし、**userName**、**password**、**integratedSecurity** を除きます)。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
