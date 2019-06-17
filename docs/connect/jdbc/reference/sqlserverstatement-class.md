---
title: SQLServerStatement クラス |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ec24963c-8b51-4838-91e9-1fbfa2347451
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0901763b2f7b6c62e365df953012c2f54dba6f6d
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66776728"
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
  
## <a name="remarks"></a>Remarks  
 SQLServerStatement クラスには、JDBC の準備されたステートメントや呼び出し可能ステートメントの基本クラスの実装メソッドも各種用意されています。 SQLServerStatement クラスの基本的な役割は、SQL ステートメントを実行し、更新数と結果セットをユーザー アプリケーションに返すことです。  
  
 このクラスは、SQLServerStatement クラス、ISQLServerStatement インターフェイス、および java.sql.Statement インターフェイスへのアンラッピングをサポートしています。 詳細については、次を参照してください。[ラッパーとインターフェイス](../../../connect/jdbc/wrappers-and-interfaces.md)します。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [JDBC Driver API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
