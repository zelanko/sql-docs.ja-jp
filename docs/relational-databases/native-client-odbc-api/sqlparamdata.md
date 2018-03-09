---
title: "SQLParamData |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQLParamData function
ms.assetid: 92349482-ea22-4a6a-8484-e9c6566794fa
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8654eda16ddea81bd1d28a7bc02b24a8b5c487b3
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="sqlparamdata"></a>SQLParamData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  SQLParamData が返されるときに、 *ValuePtrPtr* 、テーブル値パラメーターに関連付けられた、アプリケーションと SQLPutData を呼び出す必要があります*StrLen_Or_Ind*です。 場合*StrLen_Or_Ind*が 0 より大きい値を持つアプリケーションが整っていることを意味、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client を次のテーブル値パラメーター行のパラメーター データを収集します。 場合*StrLen_Or_Ind*値が 0 では、テーブル値パラメーターのデータの行を意味します。 詳細については、次を参照してください。[バインドおよび Data Transfer of Table-Valued パラメーターと列の値](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)です。  
  
 テーブル値パラメーターの詳細については、次を参照してください。[テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLParamData](http://go.microsoft.com/fwlink/?LinkId=80706)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
