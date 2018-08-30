---
title: SQLServerXAResource クラス |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: df957b79-536f-4db7-b6ac-3d59343559fc
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e7a40dc7a3f55a9c331f15783a4349e3ffbed269
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784240"
---
# <a name="sqlserverxaresource-class"></a>SQLServerXAResource クラス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  XA 分散トランザクション管理用の XAResource を表します。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **拡張:** java.lang.Object  
  
 実装 :** javax.transaction.xa.XAResource  
  
## <a name="syntax"></a>構文  
  
```  
  
public class SQLServerXAResource  
```  
  
## <a name="remarks"></a>Remarks  
 XA トランザクションは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分散トランザクション マネージャー (DTC) を使用して [!INCLUDE[msCoName](../../../includes/msconame_md.md)] に実装されます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] クラスは、DTC とのインターフェイスになる sqljdbc_xa.dll という名前の  拡張 DLL を呼び出します。 が受信する XA 呼び出し (XA_START、XA_END、XA_PREPARE など) は、対応する DTC 関数の呼び出しにマップされます。  
  
## <a name="see-also"></a>参照  
 [SQLServerXAResource のメンバー](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [JDBC Driver API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
