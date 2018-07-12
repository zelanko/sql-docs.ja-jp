---
title: SQLSetEnvAttr |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLSetEnvAttr function
ms.assetid: d4114571-feca-4330-b2e4-7bfd1050b812
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c2633c9b9c4a7810720a556daa7148f44f389b5c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37418611"
---
# <a name="sqlsetenvattr"></a>SQLSetEnvAttr
  [ODBC プログラマ リファレンス](http://go.microsoft.com/fwlink/?LinkId=45250)ODBC ドライバーを解釈する方法を定義、 **SQLSetEnvAttr**属性の ODBC 2 に書かれたアプリケーションからの仕様 *。x*または ODBC 3 *。x* API。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、これらの規則に準拠します。  
  
 によって制御される属性の 1 つ**SQLSetEnvAttr**は使用するかどうかが接続プールします。 接続プールを使用した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー、 *DriverCompletion*いずれかで接続するときに、パラメーターを SQL_DRIVER_NOPROMPT に設定する必要があります[SQLDriverConnect](sqldriverconnect.md)または**SQLConnect**します。  
  
## <a name="see-also"></a>参照  
 [SQLSetEnvAttr 関数](http://go.microsoft.com/fwlink/?LinkId=59369)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
