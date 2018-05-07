---
title: setPortNumber メソッド (SQLServerDataSource) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDataSource.setPortNumber
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 59c5fa23-bc1a-4142-af17-70e275f0b833
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5665bd5ed6f10a755f3980607995b19887908379
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="setportnumber-method-sqlserverdatasource"></a>setPortNumber メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  通信するために使用するポート番号を設定[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setPortNumber(int portNumber)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *PortNumber*  
  
 **Int**ポート番号を含む値です。  
  
## <a name="remarks"></a>解説  
 ポート番号へのソケット接続を開くときに使用される TCP/IP ポート番号は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。 PortNumber プロパティが設定されていない場合、 [getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md)メソッドは、既定値の 1433 を返します。  
  
> [!NOTE]  
>  SetPortNumber メソッドでは、任意の範囲に渡されたポート値のチェックは実行しません。 エラーをトリガーすることがなく 99999 などの無効なポート番号を渡すことができます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
