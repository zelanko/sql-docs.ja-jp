---
title: SQLServerPreparedStatement クラス |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a8481c06-fbba-432b-8c69-4f4619c20ad4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7112a20f7811a0796396045c50b1b243ed0c3802
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796951"
---
# <a name="sqlserverpreparedstatement-class"></a>SQLServerPreparedStatement クラス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  JDBC の準備されたステートメント機能の基本的な実装を表します。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **継承:** SQLServerStatement  
  
 **実装:** [ISQLServerPreparedStatement](../../../connect/jdbc/reference/isqlserverpreparedstatement-interface.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
public class SQLServerPreparedStatement  
```  
  
## <a name="remarks"></a>Remarks  
 SQLServerPreparedStatement は、任意の Java ネイティブ型および多数の Java オブジェクト型としてパラメーターを指定できるメソッドを提供します。 SQLServerPreparedStatement は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **sp_prepare** ストアド プロシージャを使用してステートメントを準備し、それ以降のそのステートメントの実行は、返されたステートメント ハンドルを再利用し、通常はユーザーが提供するさまざまなパラメーターを使用して行われます。  
  
 SQLServerPreparedStatement ではバッチ処理がサポートされており、準備されたステートメントのセットが単一のデータベースのラウンド トリップで実行され、実行時パフォーマンスが向上します。  
  
 このクラスは、SQLServerPreparedStatement クラス、ISQLServerPreparedStatement インターフェイス、java.sql.PreparedStatement インターフェイス、クラスおよびアンラッピング用 SQLServerStatement でサポートされるインターフェイスへのアンラッピングをサポートしています。 詳細については、次を参照してください。[ラッパーとインターフェイス](../../../connect/jdbc/wrappers-and-interfaces.md)します。  
  
## <a name="see-also"></a>参照  
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [JDBC Driver API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
