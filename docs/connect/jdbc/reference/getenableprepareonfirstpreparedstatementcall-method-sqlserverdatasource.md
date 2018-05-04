---
title: getEnablePrepareOnFirstPreparedStatementCall メソッド (SQLServerDataSource) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a131964479c0e2f64afa1f316344d446d1df2214
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="getenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource"></a>getEnablePrepareOnFirstPreparedStatementCall メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  値を返します**enablePrepareOnFirstPreparedStatementCall**接続プロパティです。 この構成は、false を返した場合、準備されたステートメントの最初の実行が sp_executesql を呼び出すし、sp_prepexec を呼び出すし、準備されたステートメント ハンドルを実際にセットアップが 2 つ目の実行が発生したら、ステートメントを準備できません。 次の実行は sp_execute を呼び出します。 これから解放 sp_unprepare 準備されたステートメントでの必要性閉じる場合は、ステートメントは 1 回だけ実行します。 
  
## <a name="syntax"></a>構文  
  
```
public boolean getEnablePrepareOnFirstPreparedStatementCall();  
```  
  
## <a name="return-value"></a>戻り値  
 返します、**ブール**の値、 **enablePrepareOnFirstPreparedStatementCall**接続プロパティです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>解説  
 このメソッドは、JDBC ドライバーのバージョン 6.4 から利用できるとは。
 
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
