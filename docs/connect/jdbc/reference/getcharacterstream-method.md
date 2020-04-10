---
title: getCharacterStream メソッド () | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerClob.getCharacterStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 70a5a8c8-791a-43f9-8a0e-1c390f30857c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 55f50865ce1437ca3611e08836cd6354e4d3d113
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80907421"
---
# <a name="getcharacterstream-method-"></a>getCharacterStream () メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  **CLOB** データを、Reader オブジェクトまたは文字のストリームとして返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.io.Reader getCharacterStream()  
```  
  
## <a name="return-value"></a>戻り値  
 **CLOB** データを含む Reader オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getCharacterStream メソッドは、java.sql.Clob インターフェイスの getCharacterStream メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerClob のメソッド](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob メンバー](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob クラス](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
