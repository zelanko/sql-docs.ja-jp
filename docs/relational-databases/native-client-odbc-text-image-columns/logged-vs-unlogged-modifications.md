---
title: ログ記録と Unlogged の変更 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 922d4c7be51e92b02ea904d5b4917f7ccbeec28c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85760618"
---
# <a name="logged-vs-unlogged-modifications"></a>ログに記録される変更と記録されない変更
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  アプリケーションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーが**text**、 **ntext**、および**image**の変更をログに記録しないように要求できます。 ただし、このオプションの使用には注意が必要です。 **Text**型、 **ntext**型、または**image**型のデータが重要ではなく、データ所有者がデータを回復してパフォーマンスを向上させることができない場合にのみ使用してください。  
  
 **Text**、 **ntext**、および**image**の変更のログ記録は、*属性*パラメーターを SQL_SOPT_SS_ TEXTPTR_LOGGING に設定し、 *valueptr*を SQL_TL_ON または SQL_TL_OFF に設定して、 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)を呼び出すことによって制御されます。  
  
## <a name="see-also"></a>関連項目  
 [text 列と image 列の管理](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
  
