---
title: getSchemas メソッド (String, String) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 672171ac-976f-4605-9bee-2a5e141d92cb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 76c5831547178b33854465d38cfe97dc87684d15
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47684610"
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
  
 データベース内のカタログの名前です。 空の文字列 "" の場合、結果にはカタログのないスキーマが含まれます。 **null** の場合、カタログ名は検索に使用されません。  
  
 *schemaPattern*  
  
 スキーマの名前です。 **null** の場合、スキーマ名は検索に使用されません。  
  
## <a name="return-value"></a>戻り値  
 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getURL メソッドは、java.sql.DatabaseMetaData インターフェイスの getURL メソッドで規定されています。  
  
 GetSchemas メソッドによって返される結果セットには、次の情報が含まれています。  
  
|[オブジェクト名]|型|[説明]|  
|----------|----------|-----------------|  
|TABLE_SCHEM|**String**|スキーマの名前です。|  
|TABLE_CATALOG|**String**|スキーマのカタログ名です。|  
  
 結果は、TABLE_CATALOG および TABLE_SCHEM で順序付けされます。 各行の最初の列は TABLE_SCHEM、次の列は TABLE_CATALOG です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
