---
title: "SQLServerCallableStatement クラス |Microsoft ドキュメント"
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
ms.assetid: 30710a63-c05d-47d9-9cf9-c087a1c76373
caps.latest.revision: "20"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2fb8757c3bef90d69d8ea1ea9b42720d64eefa7a
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="sqlservercallablestatement-class"></a>SQLServerCallableStatement クラス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  入力パラメーターおよび出力パラメーターと共に、呼び出すストアド プロシージャの名前を指定できます。 また、? = call( ?, ..) 構文を使用して状態の戻り値を取得することもできます。 呼び出しを = (?、..) 構文です。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **実装:** [ISQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
 **拡張:** [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
public final class SQLServerCallableStatement  
```  
  
## <a name="remarks"></a>解説  
 SQLServerCallableStatement では、入力呼び出し力パラメーターと共に、呼び出すストアド プロシージャ名を指定できます。 SQLServerCallableStatement は、使用して、戻り値の状態値を取得する機能も用意されています。、`? = call( ?, ..)`構文です。  
  
 このクラスは、SQLServerCallableStatement クラス、ISQLServerCallableStatement インターフェイス、java.sql.CallableStatement インターフェイスとクラスおよび SQLServerPreparedStatement がへのアンラッピングをサポートするインターフェイスへのアンラッピングをサポートします。 詳細については、次を参照してください。[ラッパーとインターフェイス](../../../connect/jdbc/wrappers-and-interfaces.md)です。  
  
 ときに、SQLServerCallableStatement のいずれかの set メソッドと呼ばれる型の場合に指定された型と競合する場合[registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)、最後の SQLServerCallableStatement set メソッドで指定された型を使用します。 ただし、その結果、データ型の非互換性から変換エラーが発生する可能性があります。 SQLServerCallableStatement set メソッドが呼び出されなかった場合、最初に指定された型[registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)呼び出しを使用します。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] JDBC Driver 3.0 は、結果セットの JDBC 4.0 の勧告に準拠していると、更新数が OUT パラメーターを取得する前に取得する必要があります。 結果セットと更新数が完全に処理される前に OUT パラメーターが取得された場合、処理の済んでいない結果セットと更新数はすべて失われます。  
  
## <a name="see-also"></a>参照  
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [JDBC ドライバー API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
