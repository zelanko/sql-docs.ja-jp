---
title: "setXopenStates メソッド (SQLServerDataSource) |Microsoft ドキュメント"
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
apiname: SQLServerDataSource.setXopenStates
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 9723591f-e987-426f-b70a-07f5c70dc094
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bb9d14bebdbb8f6d7e2569cd5081541ca9080431
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="setxopenstates-method-sqlserverdatasource"></a>setXopenStates メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  セット、**ブール**XOPEN 互換の状態を SQL 状態の変換が有効かどうかを示す値。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setXopenStates(boolean xopenStates)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *xopenStates*  
  
 **true** XOPEN 互換の状態を SQL 状態の変換が有効になっている場合。 それ以外の場合は、 **false**です。  
  
## <a name="remarks"></a>解説  
 XopenStates プロパティ設定されている場合**true**、 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] SQL 状態を XOPEN 互換の状態に変換されます。 既定値は**false**、SQL 99 の状態コードを生成するには、JDBC ドライバーを停止します。 XopenStates が設定されていない場合、 [getXopenStates](../../../connect/jdbc/reference/getxopenstates-method-sqlserverdatasource.md)メソッドの既定値を返します**false**です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
