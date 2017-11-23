---
title: "ログに記録されたとします。変更ログを取らない |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-text-image-columns
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- logged vs. nonlogged modifications [SQL Server Native Client]
- columns [ODBC]
- ODBC data types, image columns
- nonlogged vs. logged modifications
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 20aa5b27-4a2c-46e7-8356-beb0eebf4b7e
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2a429671be26d53fe9354e4ab986cb10ac35d35b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="logged-vs-unlogged-modifications"></a>ログに記録されたとします。記録されない変更
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  アプリケーションが要求する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー ログに記録しない**テキスト**、 **ntext**、および**イメージ**変更します。 ただし、このオプションの使用には注意が必要です。 そのような場合にのみ使用する必要があります場所、**テキスト**、 **ntext**、または**イメージ**データは重要ではないと、データの所有者がデータを回復する機能を犠牲にするパフォーマンスを向上します。  
  
 ログ記録**テキスト**、 **ntext**、および**イメージ**変更が呼び出すことによって制御される[SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)で、 *属性*パラメーターを SQL_SOPT_SS _ TEXTPTR_LOGGING に設定し、 *ValuePtr* SQL_TL_ON または SQL_TL_OFF に設定します。  
  
## <a name="see-also"></a>参照  
 [text 列と image 列の管理](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
  
