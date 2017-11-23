---
title: "SQLServerConnection クラス |Microsoft ドキュメント"
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
ms.assetid: 937292a6-1525-423e-a2b2-a18fd34c2893
caps.latest.revision: "17"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 385bef4155f4b41f181774b1559282c42ac1fbee
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="sqlserverconnection-class"></a>SQLServerConnection クラス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  JDBC の接続を表し、 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データベース。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **実装:** [ISQLServerConnection](../../../connect/jdbc/reference/isqlserverconnection-interface.md)、java.io.Serializable  
  
## <a name="syntax"></a>構文  
  
```  
  
public class SQLServerConnection  
```  
  
## <a name="remarks"></a>解説  
 SQLServerConnection では、JDBC 接続プールをサポートし、物理的な JDBC 接続または論理的な JDBC 接続のいずれかを指定できます。 SQLServerConnection が、そこから作成されたすべてのステートメントのトランザクション制御を管理し、XAResource アダプターを通じて管理される XA 分散トランザクションに参加できます。  
  
 SQLServerConnection では、準備されたステートメント ハンドルのプールを管理します。 ステートメントは 1 回だけ準備され、通常はパラメーターに対して異なるデータ値を指定し、何度も実行されます。 準備されたステートメントは、論理 (プール) 接続の終了後も維持されます。  
  
> [!NOTE]  
>  SQLServerConnection はスレッド セーフではありません。 ただし、単一の接続から作成された複数のステートメントは、同時スレッドで同時に処理することができます。  
  
 このクラスは、SQLServerConnection クラス、java.sql.connection インターフェイス、および ISQLServerConnection インターフェイスへのアンラッピングをサポートします。 詳細については、次を参照してください。[ラッパーとインターフェイス](../../../connect/jdbc/wrappers-and-interfaces.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [JDBC ドライバー API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
