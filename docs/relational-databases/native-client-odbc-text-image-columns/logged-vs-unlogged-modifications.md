---
title: ログに変更ログを取らない |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-text-image-columns
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
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
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c6ddd2f450fd2d796319aa88c89d9e1278e6a063
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43084004"
---
# <a name="logged-vs-unlogged-modifications"></a>ログに記録される変更と記録されない変更
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  アプリケーションが要求を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client ODBC ドライバー ログではなく**テキスト**、 **ntext**、および**イメージ**変更します。 ただし、このオプションの使用には注意が必要です。 そのような状況だけのために使用する必要があります、**テキスト**、 **ntext**、または**イメージ**データが重要でないと、データの所有者がデータを回復する機能のトレードオフを許容できます。高いパフォーマンス。  
  
 ログ記録**テキスト**、 **ntext**、および**イメージ**変更が呼び出すことによって制御される[SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)で、 *属性*パラメーターを SQL_SOPT_SS _ TEXTPTR_LOGGING に設定し、 *ValuePtr* SQL_TL_ON または SQL_TL_OFF に設定します。  
  
## <a name="see-also"></a>参照  
 [text 列と image 列の管理](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
  
