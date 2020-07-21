---
title: SQLServerConnectionPoolDataSource クラス | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b00e5a90-2af7-4d04-8ef8-256183777dcf
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0accd21f53a4ba1a86e4b7555be9d2ba9a087474
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921044"
---
# <a name="sqlserverconnectionpooldatasource-class"></a>SQLServerConnectionPoolDataSource クラス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  接続プール マネージャーの物理データベース接続を表します。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **拡張:** [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
 **実装:** javax.sql.ConnectionPoolDataSource  
  
## <a name="syntax"></a>構文  
  
```  
  
public class SQLServerConnectionPoolDataSource  
```  
  
## <a name="remarks"></a>解説  
 SQLServerConnectionPoolDataSource は通常、組み込みの接続プールをサポートし、物理接続を提供するための ConnectionPoolDataSource が要求される Java アプリケーション サーバー環境 (JDBC 3.0 API 仕様の接続プールを提供する Java Platform, Enterprise Edition (Java EE) アプリケーション サーバーなど) で使用されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnectionPoolDataSource のメンバー](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-members.md)   
 [JDBC Driver API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
