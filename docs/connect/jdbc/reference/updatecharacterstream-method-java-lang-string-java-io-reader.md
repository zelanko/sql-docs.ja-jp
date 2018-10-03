---
title: updateCharacterStream (java.lang.String, java.io.Reader) メソッド | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a8ec22a9-4bbd-4759-9f21-957304ef3a5e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0e0111b401f43771a15e3e7ae001931039a2ab5f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47732410"
---
# <a name="updatecharacterstream-method-javalangstring-javaioreader"></a>updateCharacterStream (java.lang.String, java.io.Reader) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列を文字ストリームの値で更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateCharacterStream(java.lang.String columnLabel,  
                                  java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnLabel*  
  
 列ラベルを含む**文字列**です。  
  
 *reader*  
  
 リーダー オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この updateCharacterStream メソッドは、java.sql.ResultSet インターフェイスの updateCharacterStream メソッドによって指定されます。  
  
 このメソッドは、Unicode 文字を Reader オブジェクトから選択したテキストおよびバイナリ列に渡します。 これには、すべてのテキスト列と **binary**、**varbinary**、**varbinary(max)**、**image**、**xml** の各列が含まれますが、**udt** 列は含まれません。  
  
 このメソッドを使用して、**イメージ**、**テキスト**、および**ntext** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データ型のパフォーマンスに影響を与える可能性があります。  
  
## <a name="see-also"></a>参照  
 [updateCharacterStream メソッド &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatecharacterstream-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
