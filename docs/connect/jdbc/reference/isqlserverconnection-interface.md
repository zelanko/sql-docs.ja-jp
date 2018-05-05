---
title: ISQLServerConnection インターフェイス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 031c01e2-2c65-4fe4-9700-fdbcc7a39f30
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4ca0e0504a7f28622ba2419545d2167ad917f784
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="isqlserverconnection-interface"></a>ISQLServerConnection インターフェイス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  JDBC の接続を表し、 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データベース。 このインターフェイスが追加されました[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]JDBC Driver 3.0 です。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **拡張:** java.sql.Connection  
  
## <a name="syntax"></a>構文  
  
```  
  
public interface ISQLServerConnection  
```  
  
## <a name="remarks"></a>解説  
 このインターフェイスはによって実装[SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)です。  
  
 このインターフェイスは、次を公開[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-特定のフィールド。  
  
|フィールド|詳細については、「|  
|-----------|-------------------------------|  
|public final static int TRANSACTION_SNAPSHOT|[TRANSACTION_SNAPSHOT](../../../connect/jdbc/reference/transaction-snapshot-field-sqlserverconnection.md)|  
|public UUID getClientConnectionId()|[getClientConnectionID()](../../../connect/jdbc/reference/getclientconnectionid-method-sqlserverconnection.md)|  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバー API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
