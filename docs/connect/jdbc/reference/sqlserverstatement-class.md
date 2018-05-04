---
title: SQLServerStatement クラス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ec24963c-8b51-4838-91e9-1fbfa2347451
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3be0aec7cec27437b20b99a8f1445315f07a32b4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlserverstatement-class"></a>SQLServerStatement クラス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  JDBC ステートメント機能の基本的な実装を表します。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **実装:** [ISQLServerStatement](../../../connect/jdbc/reference/isqlserverstatement-interface.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
public class SQLServerStatement  
```  
  
## <a name="remarks"></a>解説  
 SQLServerStatement クラスでは、準備されたステートメントや呼び出し可能ステートメント、JDBC の基本クラスの実装方法の数も提供します。 SQLServerStatement クラスの基本的な役割は、SQL ステートメントを実行して、戻り値の更新プログラムの数と結果セットをユーザー アプリケーションにします。  
  
 このクラスは、SQLServerStatement クラス、ISQLServerStatement インターフェイスおよび java.sql.Statement インターフェイスへのアンラッピングをサポートします。 詳細については、次を参照してください。[ラッパーとインターフェイス](../../../connect/jdbc/wrappers-and-interfaces.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [JDBC ドライバー API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
