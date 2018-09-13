---
title: SQLServerCallableStatement クラス |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 30710a63-c05d-47d9-9cf9-c087a1c76373
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8dca164af73506119cfaef376bcb7776708f76df
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785506"
---
# <a name="sqlservercallablestatement-class"></a>SQLServerCallableStatement クラス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  入力パラメーターおよび出力パラメーターと共に、呼び出すストアド プロシージャの名前を指定できます。 また、? = call( ?, ..) 構文を使用して状態の戻り値を取得することもできます。 呼び出しを = (?、..) 構文。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **実装:** [ISQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
 **継承:** [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
public final class SQLServerCallableStatement  
```  
  
## <a name="remarks"></a>Remarks  
 SQLServerCallableStatement を使用すると、呼び出すストアド プロシージャの名前と共に、入力および出力パラメーターを指定できます。 SQLServerCallableStatement は、使用状態の戻り値を取得する機能も用意されています。、`? = call( ?, ..)`構文。  
  
 このクラスは、SQLServerCallableStatement クラス、ISQLServerCallableStatement インターフェイス、java.sql.CallableStatement インターフェイス、クラスおよび SQLServerPreparedStatement でアンラッピングをサポートされるインターフェイスへのアンラッピングをサポートしています。 詳細については、次を参照してください。[ラッパーとインターフェイス](../../../connect/jdbc/wrappers-and-interfaces.md)します。  
  
 指定された型との競合を入力する場合、型、に対して呼び出すはメソッドを設定、SQLServerCallableStatement のいずれかと[registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)、最後の SQLServerCallableStatement set メソッドで指定された型を使用します。 ただし、その結果、データ型の非互換性から変換エラーが発生する可能性があります。 SQLServerCallableStatement の set メソッドが呼び出されなかった場合、最初の [registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) 呼び出しで指定された型が使用されます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 は、結果セットと更新数が OUT パラメーターよりも先に取得されなければならないという JDBC 4.0 の勧告に準拠しています。 結果セットと更新数が完全に処理される前に OUT パラメーターが取得された場合、処理の済んでいない結果セットと更新数はすべて失われます。  
  
## <a name="see-also"></a>参照  
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [JDBC Driver API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
