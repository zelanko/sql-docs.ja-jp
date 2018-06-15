---
title: updateBinaryStream (int, java.io.InputStream) メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1db3a975-c108-45d1-8c0d-14a094f391bd
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3682c8418ff107eb7ef7a7c91797a9d859a5f1d8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32850717"
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
  
## <a name="remarks"></a>解説  
 この updateBinaryStream メソッドは、java.sql.ResultSet インターフェイスの updateBinaryStream メソッドによって指定されます。  
  
 このメソッドを使用して、**イメージ**、**テキスト**、および**ntext** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データ型には、パフォーマンスが低下します。  
  
 このメソッドは、選択された状態に InputStream オブジェクトからバイトを渡します[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]binary、varbinary、varbinary (max)、image、xml、および udt などのバイナリ列です。 このメソッドでは、文字型の列の更新はサポートされていません。 更新するには文字型列、InputStream を使用して、 [updateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)メソッドです。  
  
## <a name="see-also"></a>参照  
 [updateBinaryStream メソッド&#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
