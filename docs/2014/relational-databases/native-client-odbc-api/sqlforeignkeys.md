---
title: SQLForeignKeys |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLForeignKeys function
ms.assetid: 6c01ce0d-30d7-4c86-8705-3ab254d8a845
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 20b48d67072919fe42661343ff133cd3ea1a8773
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176386"
---
# <a name="sqlforeignkeys"></a>SQLForeignKeys
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、外部キー制約メカニズムによってカスケード更新とカスケード削除がサポートされます。 FOREIGN KEY 制約の ON UPDATE 句や ON DELETE 句で CASCADE オプションが指定されている場合、UPDATE_RULE 列や DELETE_RULE 列に対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から SQL_CASCADE が返されます。 FOREIGN KEY 制約の ON UPDATE 句や ON DELETE 句で NO ACTION オプションが指定されている場合は、UPDATE_RULE 列や DELETE_RULE 列に対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から SQL_NO_ACTION が返されます。  
  
 ときに無効な値は、いずれかで**SQLForeignKeys**パラメーター、 **SQLForeignKeys**実行時に関係なく SQL_SUCCESS を返します。 **SQLFetch** SQL_NO_DATA が返されるこれらのパラメーターに無効な値を使用する場合。  
  
 **SQLForeignKeys**は静的サーバー カーソルで実行できます。 実行すると**SQLForeignKeys**更新可能な (動的カーソルまたはキーセット カーソル)、カーソルの種類が変更されたことを示す SQL_SUCCESS_WITH_INFO が返されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーをサポートしているレポート情報のリンク サーバー上のテーブルの 2 部構成の名前を受け入れることにより、 *FKCatalogName*と*PKCatalogName*パラメーター: *Linked_Server_Name.Catalog_Name*です。  
  
## <a name="see-also"></a>参照  
 [SQLForeignKeys 関数](http://go.microsoft.com/fwlink/?LinkId=59344)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  