---
title: SQLParamData |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLParamData function
ms.assetid: 92349482-ea22-4a6a-8484-e9c6566794fa
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a45b3b4562037e00572d2f3ea5e5fb15df497584
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43095161"
---
# <a name="sqlparamdata"></a>SQLParamData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  SQLParamData が返されるときに、 *ValuePtrPtr*テーブル値パラメーターでは、関連付けられているアプリケーションと SQLPutData を呼び出す必要があります*StrLen_Or_Ind*します。 場合*StrLen_Or_Ind* 、0 より大きい値を持つアプリケーションが整ったことになります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client を次のテーブル値パラメーター行のパラメーターのデータを収集します。 場合*StrLen_Or_Ind*の値を持つ 0 はテーブル値パラメーターのデータの行を意味します。 詳細については、次を参照してください。[バインドと Data Transfer of Table-Valued パラメーターおよび列の値](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)します。  
  
 テーブル値パラメーターの詳細については、次を参照してください。[テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)します。  
  
## <a name="see-also"></a>参照  
 [SQLParamData](http://go.microsoft.com/fwlink/?LinkId=80706)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
