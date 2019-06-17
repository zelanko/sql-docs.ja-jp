---
title: getPortNumber メソッド (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getPortNumber
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e5dc38d0-4340-4ad7-a56e-1d2a0f0fd846
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b731bf5ce8272fe72167d77b96e523cd3ede1139
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66771343"
---
# <a name="getportnumber-method-sqlserverdatasource"></a>getPortNumber メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] との通信に使用される現在のポート番号が返されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getPortNumber()  
```  
  
## <a name="return-value"></a>戻り値  
 現在のポート番号を含む **int** 値です。  
  
## <a name="remarks"></a>Remarks  
 このポート番号は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] へのソケット接続を開くときに使用される TCP/IP ポート番号です。 portNumber プロパティが設定されていない場合、getPortNumber メソッドは既定値の 1433 を返します。  
  
> [!NOTE]  
>  [SetPortNumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md)メソッドでは、任意の範囲に渡されたポート値のチェックは実行しません。 エラーをトリガーすることがなく 99999 などの無効な番号を渡すことができます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
