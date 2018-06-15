---
title: setPoolable メソッド (SQLServerStatement) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f0f798c8-cafb-4acc-b85d-2e0059c91d92
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1cc4938abaf5c281da0bae0c14d86b85883d4062
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32844437"
---
# <a name="setpoolable-method-sqlserverstatement"></a>setPoolable メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  ステートメントをプールすること、またはプールしないことを要求します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setPoolable(boolean poolable) throws SQLException  
```  
  
#### <a name="parameters"></a>パラメーター  
 *プール*  
  
 場合**true**ステートメントをプールすることを要求します。 場合**false**ステートメントをプールしないことを要求します。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 指定された値、*プール*パラメーターは、アプリケーションがステートメントをプールする必要があるかどうかを示すステートメント プール実装へのヒント。 そのヒントを使用するかどうかは、ステートメント プール マネージャーによって決定されます。  
  
 ステートメントのプール値は、ドライバーによって実装される内部ステートメント キャッシュと、アプリケーション サーバーや他のアプリケーションによって実装される外部ステートメント キャッシュの両方に適用されます。  
  
 既定では、SQLServerStatement オブジェクトは作成時にプールではありません。 SQLServerPreparedStatement や SQLServerCallableStatement オブジェクトは作成時にプールします。  
  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)を閉じたステートメントでこのメソッドが呼び出された場合にスローされます。  
  
 [isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md)かどうか、オブジェクトはプールを示す値を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
