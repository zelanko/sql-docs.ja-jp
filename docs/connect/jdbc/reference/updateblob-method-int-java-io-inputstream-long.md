---
title: updateBlob (int, java.io.InputStream, long) メソッド
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2edf9b51-63e1-4c28-afdf-2d4af593d5f7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e7e59ca60471e89da883b9fbaa4cf269ac33a0e9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47654800"
---
# <a name="updateblob-method-int-javaioinputstream-long"></a>updateBlob (int, java.io.InputStream, long) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された入力ストリームを使用して、指定された列を更新します。入力ストリームは、指定されたバイト数を持ちます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateBlob(int columnIndex,  
                       java.io.InputStream inputStream,  
                                              long length)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnIndex*  
  
 列インデックスを示す **int** です。  
  
 InputStream  
  
 InputStream オブジェクト。  
  
 *length*  
  
 ストリームの長さを示す **long** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この updateBlob メソッドは、java.sql.ResultSet インターフェイスの updateBlob メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [updateNClob メソッド &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateblob-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
