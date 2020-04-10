---
title: getCharacterStream (long, long) メソッド (SQLServerNClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5a8028bc-c877-4668-b662-0746d462040e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 69b626e84288764fbe1da34ac0a5e6430eaa8217
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80913138"
---
# <a name="getcharacterstream-method-long-long-sqlservernclob"></a>getCharacterStream (long, long) メソッド (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された位置と長さを使用して、**NCLOB** データを **Reader** オブジェクトまたは文字のストリームとして取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.io.Reader getCharacterStream(long pos,  
                                  long length)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pos*  
  
 取得する部分的な値の最初の文字へのオフセットを示す **long** です。  
  
 *length*  
  
 取得する部分的な値の文字の長さを示す **long** です。  
  
## <a name="return-value"></a>戻り値  
 **NCLOB** データを含む Reader オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getCharacterStream メソッドは、java.sql.NClob インターフェイスの getCharacterStream メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [getCharacterStream メソッド &#40;SQLServerNClob&#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlservernclob.md)   
 [SQLServerNClob のメソッド](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob のメンバー](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob クラス](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
