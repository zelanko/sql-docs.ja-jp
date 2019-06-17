---
title: SQLServerXAConnection クラス |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5ecb4bf1-b8d1-47cf-9cb1-7a18acc11ce2
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 177b10c9657c4cb8d6b37f7dec9d3b860308dcb7
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66788898"
---
# <a name="sqlserverxaconnection-class"></a>SQLServerXAConnection クラス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  分散 (XA) トランザクションに参加できる JDBC 接続を表します。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **拡張:** [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
 **実装:** javax.sql.XAConnection  
  
## <a name="syntax"></a>構文  
  
```  
  
public class SQLServerXAConnection  
```  
  
## <a name="remarks"></a>Remarks  
 SQLServerXAConnection オブジェクトは、[SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) オブジェクトを使用して分散トランザクションに参加させることができます。 中間層サーバーの一部は、通常、トランザクション マネージャーは、SQLServerXAResource オブジェクトを介して SQLServerXAConnection オブジェクトを管理します。  
  
> [!NOTE]  
>  通常、アプリケーション プログラマがこのインターフェイスを直接使用することはありません。 このインターフェイスは主に、中間層サーバーで動作しているトランザクション マネージャーによって使用されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerXAConnection のメンバー](../../../connect/jdbc/reference/sqlserverxaconnection-members.md)   
 [JDBC Driver API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
