---
title: getUser メソッド (SQLServerDataSource) |Microsoft ドキュメント
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
- SQLServerDataSource.getUser
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3513dd7f-6ae5-4010-bde0-454ac4365bce
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 35559c83e8ced2d532546d372fef5980fa90ec7e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="getuser-method-sqlserverdatasource"></a>getUser メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データ ソースへの接続に使用されるユーザー名を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getUser()  
```  
  
## <a name="return-value"></a>戻り値  
 A**文字列**ユーザー名を格納しています。  
  
## <a name="remarks"></a>解説  
 [SetUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md)メソッドのインスタンスに接続するときに使用されるユーザー名を設定[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。 ユーザー名の値が設定されていない場合、getUser メソッドは既定値の null を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
