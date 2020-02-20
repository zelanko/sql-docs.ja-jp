---
title: setObject (int, java.lang.Object) メソッド | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setObject (int, java.lang.Object)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 61f19faa-3006-4a1c-974c-55951e3b3000
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e4ab210a30080472a777d151695a04ec49ff1041
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67973384"
---
# <a name="setobject-method-int-javalangobject"></a>setObject (int, java.lang.Object) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡されたオブジェクトを使用して、指定されたパラメーターの値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setObject(int index,  
                            java.lang.Object obj)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *インデックス*  
  
 パラメーターの番号を示す **int** です。  
  
 *obj*  
  
 オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setObject メソッドは、java.sql.PreparedStatement インターフェイスの setObject メソッドで指定されています。  
  
 この setObject メソッドを呼び出す前に、指定したパラメーターが次のいずれかのメソッドを使用してアプリケーションで設定されている場合があります。  
  
-   SQLServerPreparedStatement クラスまたは SQLServerCallableStatement クラスの set\<Type> メソッド  
  
-   SQLServerPreparedStatement クラスまたは SQLServerCallableStatement クラスの setNull メソッド  
  
-   SQLServerCallableStatement クラスの [registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) メソッド  
  
 このような場合、パラメーターの型が自動的に設定されます。 アプリケーションで obj 値を NULL に設定してこの setObject メソッドを呼び出すと、ドライバーでは、パラメーターの型は以前に呼び出されたメソッドで設定された型であると見なされます。  
  
 obj 値が NULL で、そのパラメーターの型情報を特定できない場合、この setObject メソッドは、指定したパラメーターを CHAR に変換してからデータベースに送信します。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 以降、このメソッドの動作は **sendTimeAsDatetime** 接続プロパティ (「[接続プロパティの設定](../../../connect/jdbc/setting-the-connection-properties.md)」を参照) および [SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md) によって変更されます。  
  
 詳細については、「[java.sql.Time の値をサーバーに送信する方法の構成](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [setObject メソッド &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
