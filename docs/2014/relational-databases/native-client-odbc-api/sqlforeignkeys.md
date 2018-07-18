---
title: SQLForeignKeys |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLForeignKeys function
ms.assetid: 6c01ce0d-30d7-4c86-8705-3ab254d8a845
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a11cb7f1013f1ea76dbbefff1d29808ddfb4c7e9
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423103"
---
# <a name="sqlforeignkeys"></a>SQLForeignKeys
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、外部キー制約メカニズムによってカスケード更新とカスケード削除がサポートされます。 FOREIGN KEY 制約の ON UPDATE 句や ON DELETE 句で CASCADE オプションが指定されている場合、UPDATE_RULE 列や DELETE_RULE 列に対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から SQL_CASCADE が返されます。 FOREIGN KEY 制約の ON UPDATE 句や ON DELETE 句で NO ACTION オプションが指定されている場合は、UPDATE_RULE 列や DELETE_RULE 列に対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から SQL_NO_ACTION が返されます。  
  
 無効な値がいずれかに存在する場合**SQLForeignKeys**パラメーター、 **SQLForeignKeys**の実行に関係なく SQL_SUCCESS を返します。 **SQLFetch** SQL_NO_DATA が返されるこれらのパラメーターに無効な値を使用する場合。  
  
 **SQLForeignKeys**静的サーバー カーソルで実行できます。 実行しようとすると、 **SQLForeignKeys** (動的またはキーセット) 用の更新可能なカーソル、カーソルの種類が変更されたことを示す sql_success_with_info が返されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、リンク サーバー上のテーブルに関する情報のレポートをサポートの 2 つの部分名をそのまま使用して、 *FKCatalogName*と*PKCatalogName*パラメーター: *Linked_Server_Name.Catalog_Name*します。  
  
## <a name="see-also"></a>参照  
 [SQLForeignKeys 関数](http://go.microsoft.com/fwlink/?LinkId=59344)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
