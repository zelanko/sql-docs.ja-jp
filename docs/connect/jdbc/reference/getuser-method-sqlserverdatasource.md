---
title: getUser メソッド (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getUser
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3513dd7f-6ae5-4010-bde0-454ac4365bce
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8ce0fa8fb14789f6557bd4f54c48756acd2d1d87
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80910508"
---
# <a name="getuser-method-sqlserverdatasource"></a>getUser メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データ ソースへの接続に使用されるユーザー名を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getUser()  
```  
  
## <a name="return-value"></a>戻り値  
 ユーザー名を含む**文字列**です。  
  
## <a name="remarks"></a>解説  
 [setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md) メソッドでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続するときに使用されるユーザー名が設定されます。 ユーザー名の値が設定されていない場合、getUser メソッドは既定値の null を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
