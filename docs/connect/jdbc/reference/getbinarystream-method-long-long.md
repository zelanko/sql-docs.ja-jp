---
title: "getBinaryStream (long, long) メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30bc8882-04b4-4efd-95e4-7d3a2a8c1d47
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d53bb0e01198d1c4ecb5c08068be4220a34b765c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getbinarystream-method-long-long"></a>getBinaryStream (long, long) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された開始位置と長さを使用して、部分的な BLOB 値を含む入力ストリーム オブジェクトを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.io.InputStream getBinaryStream(long pos, long length)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pos*  
  
 取得する部分的な値の最初のバイトへのオフセットです。  
  
 *length*  
  
 取得する部分的な値の長さ (バイト単位) です。  
  
## <a name="return-value"></a>戻り値  
 BLOB データを格納している入力ストリームです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getBinaryStream メソッドは、java.sql.Blob インターフェイスの getBinaryStream メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerBlob のメソッド](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob のメンバー](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob クラス](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  

