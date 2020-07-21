---
title: SQLPrimaryKeys |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
author: rothja
ms.author: jroth
ms.openlocfilehash: 67a932996ccbf52f5ab21fd6aa62381184ebc510
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85021810"
---
# <a name="sqlprimarykeys"></a>SQLPrimaryKeys
  テーブルには、一意の行識別子として使用できる1つ以上の列が含まれる場合があります。また、PRIMARY KEY 制約なしで作成されたテーブルは、SQLPrimaryKeys に空の結果セットを返します。 ODBC 関数[sqlの列](sqlspecialcolumns.md)は、主キーのないテーブルの行識別子の候補を報告します。  
  
 SQLPrimaryKeys は、 *CatalogName*、 *SchemaName*、または*TableName*パラメーターの値が存在するかどうかを SQL_SUCCESS 返します。 SQLFetch では、これらのパラメーターに無効な値が使用されると SQL_NO_DATA が返されます。  
  
 SQLPrimaryKeys は、静的サーバーカーソルで実行できます。 更新可能なカーソル (動的カーソルまたはキーセットカーソル) で SQLPrimaryKeys を実行しようとすると、カーソルの種類が変更されたことを示す SQL_SUCCESS_WITH_INFO が返されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーでは、 *CatalogName*パラメーターに2つの部分で構成される名前を使用して、リンクサーバー上のテーブルに関する情報のレポートをサポートしています。 *Linked_Server_Name Catalog_Name*。  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a>SQLPrimaryKeys とテーブル値パラメーター  
 ステートメント属性 SQL_SOPT_SS_NAME_SCOPE の値が既定値の SQL_SS_NAME_SCOPE_TABLE ではなく SQL_SS_NAME_SCOPE_TABLE_TYPE の場合、SQLPrimaryKeys はテーブル型の主キー列に関する情報を返します。 SQL_SOPT_SS_NAME_SCOPE の詳細については、「 [SQLSetStmtAttr](sqlsetstmtattr.md)」を参照してください。  
  
 テーブル値パラメーターの詳細については、「[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQLPrimaryKeys 関数](https://go.microsoft.com/fwlink/?LinkId=59361)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
