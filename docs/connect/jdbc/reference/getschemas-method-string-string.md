---
title: getSchemas メソッド (String, String) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 672171ac-976f-4605-9bee-2a5e141d92cb
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0684e2ec5e840d6fbe2f45cdcb66f39feb404320
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="getschemas-method-string-string"></a>getSchemas (String, String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたカタログ名とスキーマ名を使用して、現在のデータベースで使用できるスキーマ名を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public ResultSet getSchemas(java.lang.String catalog,  
                       java.lang.String schemaPattern)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *catalog*  
  
 データベース内のカタログの名前です。 空の文字列 "" の場合、結果にはカタログのないスキーマが含まれます。 場合は**null**検索、カタログ名は使用されません。  
  
 *schemaPattern*  
  
 スキーマの名前です。 場合は**null**検索、スキーマ名は使用されません。  
  
## <a name="return-value"></a>戻り値  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getSchemas メソッドは、java.sql.DatabaseMetaData インターフェイスの getSchemas メソッドによって指定されます。  
  
 GetSchemas メソッドによって返される結果セットには、次の情報が含まれています。  
  
|名前|型|Description|  
|----------|----------|-----------------|  
|TABLE_SCHEM|**文字列**|スキーマの名前。|  
|TABLE_CATALOG|**文字列**|スキーマのカタログ名です。|  
  
 結果は、TABLE_CATALOG および TABLE_SCHEM で順序します。 各行の最初の列は TABLE_SCHEM、次の列は TABLE_CATALOG です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
