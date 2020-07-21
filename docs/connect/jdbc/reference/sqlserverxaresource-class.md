---
title: SQLServerXAResource クラス | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: df957b79-536f-4db7-b6ac-3d59343559fc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 048b9a2a69b33bccc60b35ab70bd954751237605
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925697"
---
# <a name="sqlserverxaresource-class"></a>SQLServerXAResource クラス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  XA 分散トランザクション管理用の XAResource を表します。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **拡張:** java.lang.Object  
  
 **実装:** javax.transaction.xa.XAResource  
  
## <a name="syntax"></a>構文  
  
```  
  
public class SQLServerXAResource  
```  
  
## <a name="remarks"></a>解説  
 XA トランザクションは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分散トランザクション マネージャー (DTC) を使用して [!INCLUDE[msCoName](../../../includes/msconame_md.md)] に実装されます。 SQLServerXAResource クラスは、DTC とのインターフェイスになる sqljdbc_xa.dll という名前の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 拡張 DLL を呼び出します。 SQLServerXAResource が受信する XA 呼び出し (XA_START、XA_END、XA_PREPARE など) は、対応する DTC 関数の呼び出しにマップされます。  
  
## <a name="see-also"></a>参照  
 [SQLServerXAResource のメンバー](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [JDBC Driver API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
