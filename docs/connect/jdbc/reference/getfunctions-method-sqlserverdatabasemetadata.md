---
title: "getFunctions メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
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
ms.assetid: 44335cbd-c84d-4ef3-a6a1-fca7eb7ec768
caps.latest.revision: "20"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d09162647b6d5a4076bb60b3bf05e1e90eb27dee
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getfunctions-method-sqlserverdatabasemetadata"></a>getFunctions メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  システム関数およびユーザー関数の記述を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public ResultSet getFunctions(java.lang.String catalog,  
                       java.lang.String schemaPattern,  
                       java.lang.String functionNamePattern)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *カタログ*  
  
 データベース内のカタログの名前です。 空の文字列 "" の場合、結果にはカタログのない関数が含まれます。 場合は**null**検索、カタログ名は使用されません。  
  
 *schemaPattern*  
  
 スキーマの名前です。 空の文字列 "" の場合、結果にはスキーマのない関数が含まれます。 場合は**null**検索、スキーマ名は使用されません。  
  
 *functionNamePattern*  
  
 関数の名前。  
  
## <a name="return-value"></a>戻り値  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getFunctions メソッドは、java.sql.DatabaseMetaData インターフェイスの getFunctions メソッドによって指定されます。  
  
 このメソッドは、指定されたスキーマ名および関数名に一致するシステム関数およびユーザー関数だけを返します。  
  
> [!IMPORTANT]  
>  返される結果セットには、呼び出し元のユーザーに、実行するためのアクセス許可がない関数が含まれることがあります。  
  
 各関数の記述には、次の列が含まれます。  
  
|名前|型|Description|  
|----------|----------|-----------------|  
|FUNCTION_CAT|**文字列**|関数が存在するデータベースの名前です。|  
|FUNCTION_SCHEM|**文字列**|関数が存在するスキーマの名前です。|  
|FUNCTION_NAME|**文字列**|関数の名前です。|  
|NUM_INPUT_PARAMS|**int**|今後の使用のために予約されています。現在は -1 の値を返します。|  
|NUM_OUTPUT_PARAMS|**int**|今後の使用のために予約されています。現在は -1 の値を返します。|  
|NUM_RESULT_SETS|**int**|今後の使用のために予約されています。現在は -1 の値を返します。|  
|REMARKS|**文字列**|関数についてのコメントです。|  
|FUNCTION_TYPE|**短い**|関数の種類です。 次の値のいずれかを指定できます。<br /><br /> SQL_PT_UNKNOWN (0)<br /><br /> SQL_PT_PROCEDURE (1)<br /><br /> SQL_PT_FUNCTION (2)|  
  
 返される結果セット内のすべての記述は、FUNCTION_CAT、FUNCTION_SCHEM、FUNCTION_NAME、および SPECIFIC_NAME で順序付けされます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
