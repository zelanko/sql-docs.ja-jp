---
title: setNCharacterStream メソッドを java.io.Reader オブジェクトの長い |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 36396dc9-f109-4da0-bd64-726704046bbf
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a3d32bdf91cfe9ddbbdc8e3bb85e101943aebcf4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47736271"
---
# <a name="setncharacterstream-method-int-javaioreader-long"></a>setNCharacterStream (int, java.io.Reader, long) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターを、指定された java.io.Reader オブジェクトに設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setNCharacterStream(int parameterIndex,  
                                                  java.io.Reader value,  
                                                                long length)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *parameterIndex*  
  
 パラメーターのインデックスを示す **int** です。  
  
 *value*  
  
 パラメーター値を含む  オブジェクトです。  
  
 *length*  
  
 パラメーター値の文字数を示す  です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この setNCharacterStream メソッドは、java.sql.PreparedStatement インターフェイスの setNCharacterStream メソッドによって指定されます。  
  
 このメソッドを使用する必要があります**NCHAR**、 **NVARCHAR**、 **NTEXT**、および**XML**データ型。  
  
 ストリームの長さが、*length* パラメーターで指定された長さと異なる場合は、行の更新または挿入時に JDBC ドライバーが例外をスローします。  
  
 ストリームの長さが不明である場合、*length* パラメーターを -1 に設定して、ドライバーが長さに関係なくストリームを受け入れるように指定できます。 sqljdbc4.jar を使用する場合、アプリケーションで長さが不明なストリームを使用して列を更新するときには、JDBC 4.0 メソッドの [updateCharacterStream メソッド &#40;int, java.io.Reader&#41;](../../../connect/jdbc/reference/setncharacterstream-method-int-java-io-reader.md) を使用することをお勧めします。  
  
## <a name="see-also"></a>参照  
 [setCharacterStream &#40;SQLServerPreparedStatement&#41; メソッド](../../../connect/jdbc/reference/setncharacterstream-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
