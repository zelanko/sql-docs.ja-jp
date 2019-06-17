---
title: acceptsURL メソッド (SQLServerDriver) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDriver.acceptsURL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fc744566-7191-4b15-9f76-b4b8087fb14a
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 3ca37a11eba988f0a4b65281ca6f6f4b0e83863f
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66783534"
---
# <a name="acceptsurl-method-sqlserverdriver"></a>acceptsURL メソッド (SQLServerDriver)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された URL が有効であるかどうかを確認します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean acceptsURL(java.lang.String url)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *url*  
  
 A**文字列**値の URL を含むデータベースに接続するために使用します。  
  
## <a name="return-value"></a>戻り値  
 渡された URL が有効である場合は **true** です。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この acceptsURL メソッドは、java.sql.Driver インターフェイスで acceptsURL メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDriver のメソッド](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [SQLServerDriver のメンバー](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [SQLServerDriver クラス](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
