---
title: updateNCharacterStream (java.lang.String, java.io.Reader) メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 504d7d06-0227-45e1-8b01-899c3e6006e8
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 94f50da3e2d042d3570455c75a1bb193f25cae73
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32849287"
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
  
 A**文字列**列ラベルを格納しています。  
  
 *リーダー*  
  
 リーダー オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateNCharacterStream メソッドは、java.sql.ResultSet インターフェイスの updateNCharacterStream メソッドによって指定されます。  
  
 このメソッドは、選択されたリーダー オブジェクトから Unicode 文字を渡します**nchar**、 **nvarchar (max)**、 **ntext**と**xml**列です。 このメソッドを他のデータ型の列で使用すると、例外がスローされます。  
  
## <a name="see-also"></a>参照  
 [updateNCharacterStream メソッド&#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
