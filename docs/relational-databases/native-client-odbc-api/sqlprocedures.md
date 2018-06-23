---
title: SQLProcedures |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLProcedures function
ms.assetid: ec41f017-f5e0-40ef-913a-65d206068631
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 95eced372cab2e6eb0807958f4fa871feaa4bf19
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2018
ms.locfileid: "35697493"
---
# <a name="sqlprocedures"></a>SQLProcedures
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャは値を返します。 **SQLProcedures**はのレポートは、結果セット列 PROCEDURE_TYPE です。  
  
 **SQLProcedures**値が存在するかどうかに関係なく SQL_SUCCESS を返します*CatalogName、SchemaName,* または*ProcName*パラメーター。 **SQLFetch** SQL_NO_DATA が返されるこれらのパラメーターに無効な値を使用する場合。  
  
 **SQLProcedures**は静的サーバー カーソルで実行できます。 実行すると**SQLProcedures**更新可能な (動的カーソルまたはキーセット カーソル) では、カーソルの種類が変更されたことを示す SQL_SUCCESS_WITH_INFO を返します。  
  
 **SQLProcedures**名前に一致するすべてのプロシージャに関する情報を返します*ProcName*現在のユーザーがまたはが現在のユーザーに付与されて VIEW DEFINITION 権限を実行することができます。  
  
## <a name="see-also"></a>参照  
 [SQLProcedures 関数](http://go.microsoft.com/fwlink/?LinkId=59364)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
