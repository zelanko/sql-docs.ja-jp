---
title: SQLForeignKeys |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLForeignKeys function
ms.assetid: 6c01ce0d-30d7-4c86-8705-3ab254d8a845
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d59eb895b735771a94fa04745b492fc68eb2ea74
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63014514"
---
# <a name="sqlforeignkeys"></a>SQLForeignKeys
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、外部キー制約メカニズムによってカスケード更新とカスケード削除がサポートされます。 FOREIGN KEY 制約の ON UPDATE 句や ON DELETE 句で CASCADE オプションが指定されている場合、UPDATE_RULE 列や DELETE_RULE 列に対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から SQL_CASCADE が返されます。 FOREIGN KEY 制約の ON UPDATE 句や ON DELETE 句で NO ACTION オプションが指定されている場合は、UPDATE_RULE 列や DELETE_RULE 列に対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から SQL_NO_ACTION が返されます。  
  
 無効な値がいずれかに存在する場合**SQLForeignKeys**パラメーター、 **SQLForeignKeys**の実行に関係なく SQL_SUCCESS を返します。 **SQLFetch** SQL_NO_DATA が返されるこれらのパラメーターに無効な値を使用する場合。  
  
 **SQLForeignKeys**静的サーバー カーソルで実行できます。 実行しようとすると、 **SQLForeignKeys** (動的またはキーセット) 用の更新可能なカーソル、カーソルの種類が変更されたことを示す sql_success_with_info が返されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、リンク サーバー上のテーブルに関する情報のレポートをサポートの 2 つの部分名をそのまま使用して、 *FKCatalogName*と*PKCatalogName*パラメーター。*Linked_Server_Name.Catalog_Name*します。  
  
## <a name="see-also"></a>参照  
 [SQLForeignKeys 関数](https://go.microsoft.com/fwlink/?LinkId=59344)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
