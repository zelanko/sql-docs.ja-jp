---
title: getBinaryStream メソッド () | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerBlob.getBinaryStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0c8f7741-daba-4c04-adc0-8d76345a899a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cd4742b7c327899d8f3f7a0ce2a6d091a74eee03
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921668"
---
# <a name="getbinarystream-method-"></a>getBinaryStream () メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  BLOB からデータを読み取る入力ストリームを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.io.InputStream getBinaryStream()  
```  
  
## <a name="return-value"></a>戻り値  
 BLOB データを格納している入力ストリームです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getBinaryStream メソッドは、java.sql.Blob インターフェイスの getBinaryStream メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerBlob のメソッド](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob のメンバー](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob クラス](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
