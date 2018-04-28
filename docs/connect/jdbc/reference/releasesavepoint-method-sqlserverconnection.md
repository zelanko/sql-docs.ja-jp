---
title: releaseSavepoint メソッド (SQLServerConnection) |Microsoft ドキュメント
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
ms.topic: article
apiname:
- SQLServerConnection.releaseSavepoint
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b6b625ea-c7ce-4a32-a9e0-6d2b4321bfd8
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0b4946cd35af3ead9c0ba357a895ffd1806e7ff7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="releasesavepoint-method-sqlserverconnection"></a>releaseSavepoint メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  削除、指定された[SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md)現在のトランザクションからのオブジェクト。  
  
> [!NOTE]  
>  このメソッドは現在サポートされていません、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]です。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void releaseSavepoint(java.sql.Savepoint savepoint)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *セーブポイント*  
  
 削除するセーブポイント オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この releaseSavepoint メソッドは、java.sql.Connection インターフェイスの releaseSavepoint メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
