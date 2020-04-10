---
title: setCharacterStream メソッド (SQLServerNClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 09042ee9-dfb1-4d0b-82bd-d1224b0aea80
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a84aac6a02e3fabac2774a41ab8dfc8e99af8b25
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927195"
---
# <a name="setcharacterstream-method-sqlservernclob"></a>setCharacterStream メソッド (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この **java.sql.NClob** オブジェクトが表す **NCLOB** 値の指定された位置から Unicode 文字のストリームを書き込むために使用するストリームを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.io.Writer setCharacterStream(long pos)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pos*  
  
 **NCLOB** 値への書き込みを開始する位置です。最初の位置は 1 です。  
  
## <a name="return-value"></a>戻り値  
 Unicode エンコード文字を書き込むことができるストリームを表す Writer オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setCharacterStream メソッドは、java.sql.NClob インターフェイスの setCharacterStream メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerNClob のメソッド](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob のメンバー](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob クラス](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
