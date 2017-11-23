---
title: "SQLServerPreparedStatement クラス |Microsoft ドキュメント"
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
ms.assetid: a8481c06-fbba-432b-8c69-4f4619c20ad4
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ddd71b05282d74177dced2eb6c750a7f667563a8
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="sqlserverpreparedstatement-class"></a>SQLServerPreparedStatement クラス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  JDBC の準備されたステートメント機能の基本的な実装を表します。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **拡張:** SQLServerStatement  
  
 **実装:** [ISQLServerPreparedStatement](../../../connect/jdbc/reference/isqlserverpreparedstatement-interface.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
public class SQLServerPreparedStatement  
```  
  
## <a name="remarks"></a>解説  
 SQLServerPreparedStatement は、Java のネイティブ型および多数の Java オブジェクト型としてパラメーターを指定するのに便利なメソッドを提供します。 SQLServerPreparedStatement を使用してステートメントを準備、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **sp_prepare**ストアド プロシージャとし、返されたステートメントが各以降を実行するため、通常を使用してステートメントのさまざまな処理を再利用ユーザーによって提供されるパラメーター。  
  
 SQLServerPreparedStatement バッチ処理をサポートするには、ここで準備されたステートメントのセットで実行されます 1 つのデータベース ラウンド トリップは、実行時のパフォーマンスを向上させるためにします。  
  
 このクラスは、SQLServerPreparedStatement クラス、ISQLServerPreparedStatement インターフェイス、java.sql.PreparedStatement インターフェイスとクラスおよびアンラッピング用 SQLServerStatement でサポートされるインターフェイスへのアンラッピングをサポートします。 詳細については、次を参照してください。[ラッパーとインターフェイス](../../../connect/jdbc/wrappers-and-interfaces.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [JDBC ドライバー API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
