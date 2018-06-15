---
title: getSuperTables メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSuperTables
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 085461de-367b-4832-88aa-010813d2bc41
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0f81be238af46d232adc2870f0ce349f97e89588
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32838738"
---
# <a name="getsupertables-method-sqlserverdatabasemetadata"></a>getSuperTables メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベース内の特定のスキーマで定義されたテーブルの階層の記述を取得します。  
  
> [!NOTE]  
>  このメソッドは、現在ではサポートされません、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]です。 このメソッドを使用すると、常に空の結果セットが返されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.ResultSet getSuperTables(java.lang.String catalog,  
                                         java.lang.String schemaPattern,  
                                         java.lang.String tableNamePattern)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *catalog*  
  
 A**文字列**カタログ名を格納しています。  
  
 *schemaPattern*  
  
 A**文字列**スキーマ名のパターンを格納しています。  
  
 *tableNamePattern*  
  
 A**文字列**テーブル名のパターンを格納しています。  
  
## <a name="return-value"></a>戻り値  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getSuperTables メソッドは、java.sql.DatabaseMetaData インターフェイスの getSuperTables メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
