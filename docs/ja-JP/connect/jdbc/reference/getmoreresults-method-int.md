---
title: getMoreResults (int) メソッド |Microsoft ドキュメント
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
- SQLServerStatement.getMoreResults (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6419e5a8-8b3a-4d5b-8226-95865c52c723
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 36a9cf3bfb2b6032694f9e33895b379bd83713ec
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="getmoreresults-method-int"></a>getMoreResults (int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この次の結果に移動[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクトと、現在開いている結果を扱いますが、指定したモードで指定された指示に従ってオブジェクトを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final boolean getMoreResults(int mode)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *モード*  
  
 **Int**現在開いている結果セット オブジェクトを処理する方法を示すです。 次の定数のいずれかを指定する必要があります。  
  
 CLOSE_CURRENT_RESULT  
  
 KEEP_CURRENT_RESULT (JDBC ドライバーではサポートされていません)  
  
 CLOSE_ALL_RESULTS  
  
## <a name="return-value"></a>戻り値  
 **true**返された結果が結果セットである場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getMoreResults メソッドは、java.sql.Statement インターフェイスの getMoreResults メソッドによって指定されます。  
  
 指定したとおりに動作結果が取得されるまで、getMoreResults メソッドを呼び出すと、*モード*引数と次の結果に移動します。  
  
> [!NOTE]  
>  JDBC ドライバーは、定数 KEEP_CURRENT_RESULT の使用をサポートしていません。 この定数を使用すると、例外がスローされます。  
  
## <a name="see-also"></a>参照  
 [getMoreResults メソッド&#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)   
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
