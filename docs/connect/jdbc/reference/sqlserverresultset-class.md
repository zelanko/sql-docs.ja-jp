---
title: SQLServerResultSet クラス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: eaffcff1-286c-459f-83da-3150778480c9
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 671eda7647b1381feeedcf76c9cca1a81d8fc267
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32846697"
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
  
## <a name="remarks"></a>解説  
 結果セットには、クライアント側とサーバー側の 2 種類があります。  
  
 クライアント側の結果セットは、結果がクライアントのプロセス メモリに収まる場合に使用されます。 これらの結果が最も高速なパフォーマンスを提供し、によって読み取られた、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]データベースから完全にします。 この結果セットでは、サーバー側カーソルを作成するオーバーヘッドが生じることによってデータベースにさらに負荷がかかることはありません。 ただし、これらの結果セットは更新できません。  
  
 サーバー側の結果セットは、結果がクライアントのプロセス メモリに収まらない場合、または結果セットを更新可能にする場合に使用できます。 このような結果セットでは、JDBC ドライバーによってサーバー側カーソルが作成され、ユーザーがカーソルをスクロールすると、結果セットの行がユーザーに意識させることなくフェッチされます。  
  
 SQLServerResultSet クラスは、Java のネイティブ データ型および多数の Java オブジェクト型を使用して結果セットを更新できるように多くのメソッドを提供します。  
  
 このクラスは、SQLServerResultSet クラス、ISQLServerResultSet インターフェイス、および java.sql.ResultSet インターフェイスへのアンラッピングをサポートします。 詳細については、次を参照してください。[ラッパーとインターフェイス](../../../connect/jdbc/wrappers-and-interfaces.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [JDBC ドライバー API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
