---
title: updateBinaryStream (int, java.io.InputStream) メソッド | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1db3a975-c108-45d1-8c0d-14a094f391bd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9ee42a7b0941fb3d485aae708a709a4f741d9825
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47782870"
---
# <a name="updatebinarystream-method-int-javaioinputstream"></a>updateBinaryStream (int, java.io.InputStream) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列をバイナリ ストリーム値で更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateBinaryStream(int columnIndex,  
                               java.io.InputStream x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnIndex*  
  
 列インデックスを示す **int** です。  
  
 *x*  
  
 InputStream オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この updateBinaryStream メソッドは、java.sql.ResultSet インターフェイスの updateBinaryStream メソッドによって指定されます。  
  
 このメソッドを使用して、**イメージ**、**テキスト**、および**ntext** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データ型、パフォーマンスに影響を与える可能性があります。  
  
 このメソッドは、InputStream オブジェクトからのバイトを、binary、varbinary、varbinary(max)、image、xml、udt など、選択した [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] バイナリ列に渡します。 このメソッドでは、文字型の列の更新はサポートされていません。 InputStream で文字型の列を更新するには、[updateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md) メソッドを使用します。  
  
## <a name="see-also"></a>参照  
 [updateBinaryStream メソッド &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
