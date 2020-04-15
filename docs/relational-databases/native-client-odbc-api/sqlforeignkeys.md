---
title: SQL 外来キー |マイクロソフトドキュメント
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b934ec05cf5f7b908efe83eeeb68bb358cd45156
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298492"
---
# <a name="sqlforeignkeys"></a>SQLForeignKeys
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、外部キー制約メカニズムによってカスケード更新とカスケード削除がサポートされます。 FOREIGN KEY 制約の ON UPDATE 句や ON DELETE 句で CASCADE オプションが指定されている場合、UPDATE_RULE 列や DELETE_RULE 列に対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から SQL_CASCADE が返されます。 FOREIGN KEY 制約の ON UPDATE 句や ON DELETE 句で NO ACTION オプションが指定されている場合は、UPDATE_RULE 列や DELETE_RULE 列に対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から SQL_NO_ACTION が返されます。  
  
 **SQLForeignKeys**パラメーターに無効な値が存在する場合 **、SQLForeignKeys は**実行時にSQL_SUCCESSを返します。 **SQLFetch**は、これらのパラメーターで無効な値が使用されている場合にSQL_NO_DATAを返します。  
  
 **SQLForeign キーは**、静的サーバー カーソルで実行できます。 更新可能な (動的またはキーセット) カーソルに対して**SQLForeignKeys**を実行しようとすると、カーソルの種類が変更されたことを示すSQL_SUCCESS_WITH_INFOが返されます。  
  
 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント ODBC ドライバーは *、FKCatalogName*パラメーターと*PKCatalogName*パラメーターの 2 つの部分から構成される名前を受け取ることによって、リンク サーバー上のテーブルのレポート情報*Linked_Server_Nameを*サポートCatalog_Name。  
  
## <a name="see-also"></a>参照  
 [関数の外来キー](https://go.microsoft.com/fwlink/?LinkId=59344)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
