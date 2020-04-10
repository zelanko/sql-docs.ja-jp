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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0b34194a7c9f2d203e2a73006f2b2dade59dd0df
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920726"
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
  
|方法|詳細については、「|  
|------------|-------------------------------|  
|microsoft.sql.DateTimeOffset getDateTimeOffset(int)|[getDateTimeOffset(int)](../../../connect/jdbc/reference/getdatetimeoffset-method-int.md)|  
|microsoft.sql.DateTimeOffset getDateTimeOffset(String)|[getDateTimeOffset(String)](../../../connect/jdbc/reference/getdatetimeoffset-method-string.md)|  
|void setDateTimeOffset(String, microsoft.sql.DateTimeOffset)|[setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlservercallablestatement.md)|  
  
## <a name="see-also"></a>参照  
 [JDBC Driver API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
