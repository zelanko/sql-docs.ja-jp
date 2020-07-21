---
title: addBatch メソッド (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.addBatch (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 093f6c3b-49a6-4043-9993-bd0482de04dd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 748828e4d58afa1fd9c5ee637e702a2403400b7a
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923019"
---
# <a name="addbatch-method-javalangstring"></a>addBatch (java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された SQL コマンドを、[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) オブジェクトの現在のコマンド一覧に追加します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void addBatch(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sql*  
  
 SQL ステートメントを含む**文字列**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この addBatch メソッドは、java.sql.Statement インターフェイスの addBatch メソッドで指定されています。  
  
 SQLServerPreparedStatement オブジェクトが作成される際、オブジェクトの SQL ステートメントが指定されるため、このメソッドを呼び出すと例外が発生します。  
  
## <a name="see-also"></a>参照  
 [addBatch メソッド &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/addbatch-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
