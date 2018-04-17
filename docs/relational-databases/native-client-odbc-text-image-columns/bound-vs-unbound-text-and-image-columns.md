---
title: Vs をバインドします。テキストとイメージの列をバインド解除されました |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-text-image-columns
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: ffd3442e-d880-46e9-b848-2365a09a2406
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b8677ba4369063f5364410799c3ca4f7bb75f267
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Vs をバインドします。バインドされない Text、Image 列
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  サーバー カーソルを使用するときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーはバインドされていないため、データを転送しないように最適化されて**テキスト**、 **ntext**、または**イメージ**時に列**SQLFetch**を実行します。 **テキスト**、 **ntext**、または**イメージ**データが実際には取得されません、サーバーからアプリケーションの問題まで[SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md)列にします。  
  
 多くのアプリケーションを書き込むことができるようにありません**テキスト**、 **ntext**、または**イメージ**ユーザーは単にスクロール カーソルの間のデータが表示されます。 アプリケーションが呼び出すことができますし、ユーザーは、詳細情報を表示する行を選択するときに**SQLGetData**を取得する、**テキスト**、 **ntext**、または**イメージ**データ。 こうと送信、**テキスト**、 **ntext**、または**イメージ**の任意のユーザーがいないを選択し、その行のデータが非常に大量のデータの転送を防ぐ。  
  
## <a name="see-also"></a>参照  
 [テキストとイメージの列を管理します。](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)   
 [カーソルの動作](../../relational-databases/native-client-odbc-cursors/cursor-behaviors.md)  
  
  
