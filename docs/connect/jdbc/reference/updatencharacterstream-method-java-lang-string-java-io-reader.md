---
title: updateNCharacterStream (java.lang.String, java.io.Reader) メソッド | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 504d7d06-0227-45e1-8b01-899c3e6006e8
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c7139fbe6caff5e8f30bb93aa6739db0f713a120
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66798440"
---
# <a name="updatencharacterstream-method-javalangstring-javaioreader"></a>updateNCharacterStream (java.lang.String, java.io.Reader) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列を文字ストリームの値で更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateNCharacterStream(java.lang.String columnLabel,  
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
 この updateNCharacterStream メソッドは、java.sql.ResultSet インターフェイスの updateNCharacterStream メソッドによって指定されます。  
  
 このメソッドは、選択するリーダー オブジェクトから Unicode 文字を渡します**nchar**、 **nvarchar (max)** 、 **ntext**と**xml**列。 このメソッドを他のデータ型の列で使用すると、例外がスローされます。  
  
## <a name="see-also"></a>参照  
 [updateNCharacterStream メソッド &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
