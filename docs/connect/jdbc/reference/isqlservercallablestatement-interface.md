---
title: ISQLServerCallableStatement インターフェイス | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 030a1631-cfcd-41e0-beb5-47f93c01e8e0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e30758f99b3b3aa1b40319fda91760b253d17a9a
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67977495"
---
# <a name="isqlservercallablestatement-interface"></a>ISQLServerCallableStatement インターフェイス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  JDBC の呼び出し可能ステートメントを表します。 このインターフェイスは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 で追加されました。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **継承:** java.sql.CallableStatement、[ISQLServerPreparedStatement](../../../connect/jdbc/reference/isqlserverpreparedstatement-interface.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
public interface ISQLServerCallableStatement  
```  
  
## <a name="remarks"></a>解説  
 このインターフェイスは、[SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)によって実装されています。  
  
 このインターフェイスでは、次の [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 固有のメソッドが公開されます。  
  
|Method|詳細については、「|  
|------------|-------------------------------|  
|microsoft.sql.DateTimeOffset getDateTimeOffset(int)|[getDateTimeOffset(int)](../../../connect/jdbc/reference/getdatetimeoffset-method-int.md)|  
|microsoft.sql.DateTimeOffset getDateTimeOffset(String)|[getDateTimeOffset(String)](../../../connect/jdbc/reference/getdatetimeoffset-method-string.md)|  
|void setDateTimeOffset(String, microsoft.sql.DateTimeOffset)|[setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlservercallablestatement.md)|  
  
## <a name="see-also"></a>参照  
 [JDBC Driver API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
