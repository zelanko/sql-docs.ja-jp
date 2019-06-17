---
title: getDisableStatementPooling メソッド (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 607d729726c421030f4f77247b4e0090c900744c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66776825"
---
# <a name="getdisablestatementpooling-method-sqlserverdatasource"></a>getDisableStatementPooling メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  値を返します**disableStatementPooling**接続プロパティです。 この設定は、ステートメントのプールが有効になっているかどうか、またはこの接続ではなくを制御します。

  
## <a name="syntax"></a>構文  
  
```
public boolean getDisableStatementPooling();  
```  
  
## <a name="return-value"></a>戻り値  
 A**ブール**の値を格納している**disableStatementPooling**接続プロパティです。
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 このメソッドは、JDBC driver 6.4 から利用できるとは。
 
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
