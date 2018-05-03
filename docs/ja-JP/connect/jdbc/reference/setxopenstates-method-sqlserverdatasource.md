---
title: setXopenStates メソッド (SQLServerDataSource) |Microsoft ドキュメント
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
ms.topic: conceptual
apiname:
- SQLServerDataSource.setXopenStates
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9723591f-e987-426f-b70a-07f5c70dc094
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d33a442e5847cf56f443142471cc6ad68d610ef
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
  
  
