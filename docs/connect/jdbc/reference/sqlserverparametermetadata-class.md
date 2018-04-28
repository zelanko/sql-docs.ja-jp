---
title: SQLServerParameterMetaData クラス |Microsoft ドキュメント
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
ms.assetid: 546290e0-9411-4a2b-aa36-61251e70e9cf
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 54e6c4fd85ed8f658019d6a01a394317f764c9af
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sqlserverparametermetadata-class"></a>SQLServerParameterMetaData クラス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  準備されたステートメントのパラメーターのメタデータを表します。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **拡張:** java.lang.Object  
  
 **実装:** java.sql.ParameterMetaData  
  
## <a name="syntax"></a>構文  
  
```  
  
public class SQLServerParameterMetaData  
```  
  
## <a name="remarks"></a>解説  
 パラメーターのメタデータを取得するために、準備されたステートメントは SET FMT ONLY を指定して実行されます。 呼び出し可能ステートメントで sp_sproc_columns が呼び出され、プロシージャ パラメーターの名前とメタデータが取得されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerParameterMetaData のメンバー](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [JDBC ドライバー API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
