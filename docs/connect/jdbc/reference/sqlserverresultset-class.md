---
title: SQLServerResultSet クラス |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: eaffcff1-286c-459f-83da-3150778480c9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 71513f5e8006adffdb46b249f6358030d11b95a6
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801508"
---
# <a name="sqlserverresultset-class"></a>SQLServerResultSet クラス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  JDBC 結果セットを表します。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **実装:** [ISQLServerResultSet](../../../connect/jdbc/reference/isqlserverresultset-interface.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
public final class SQLServerResultSet  
```  
  
## <a name="remarks"></a>Remarks  
 結果セットには、クライアント側とサーバー側の 2 種類があります。  
  
 クライアント側の結果セットは、結果がクライアントのプロセス メモリに収まる場合に使用されます。 このような結果の場合、パフォーマンスが最も高くなり、結果全体が [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] によってデータベースから読み取られます。 この結果セットでは、サーバー側カーソルを作成するオーバーヘッドが生じることによってデータベースにさらに負荷がかかることはありません。 ただし、これらの結果セットは更新できません。  
  
 サーバー側の結果セットは、結果がクライアントのプロセス メモリに収まらない場合、または結果セットを更新可能にする場合に使用できます。 このような結果セットでは、JDBC ドライバーによってサーバー側カーソルが作成され、ユーザーがカーソルをスクロールすると、結果セットの行がユーザーに意識させることなくフェッチされます。  
  
 SQLServerResultSet クラスは、Java のネイティブ データ型および多数の Java オブジェクト型を使用して結果セットを更新できるさまざまなメソッドを提供します。  
  
 このクラスは、SQLServerResultSet クラス、ISQLServerResultSet インターフェイス、および java.sql.ResultSet インターフェイスへのアンラッピングをサポートしています。 詳細については、次を参照してください。[ラッパーとインターフェイス](../../../connect/jdbc/wrappers-and-interfaces.md)します。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [JDBC Driver API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
