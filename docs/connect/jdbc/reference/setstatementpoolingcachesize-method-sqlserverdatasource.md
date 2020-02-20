---
title: setStatementPoolingCacheSize メソッド (SQLServerDataSource) | Microsoft Docs
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
ms.openlocfilehash: 9b4ab3a1b0d6f76cd3918b20460c41d66e9616da
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67972773"
---
# <a name="setstatementpoolingcachesize-method-sqlserverdatasource"></a>setStatementPoolingCacheSize メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この接続のために準備されたステートメント キャッシュのサイズが設定されます。 disableStatementPooling が false に設定され、値が 0 より大きい場合に機能します。
  
## <a name="syntax"></a>構文  
  
```

public void setStatementPoolingCacheSize(boolean statementPoolingCacheSize);  
```  
  
#### <a name="parameters"></a>パラメーター  
 *statementPoolingCacheSize*  
  
 **statementPoolingCacheSize** 接続プロパティの新しい値です。  

## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>解説  
 このメソッドは、JDBC ドライバー バージョン 6.4 以降で使用できます。
 
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
