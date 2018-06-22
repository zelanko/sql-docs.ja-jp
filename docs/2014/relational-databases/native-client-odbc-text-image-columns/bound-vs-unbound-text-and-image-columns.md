---
title: Vs をバインドします。テキストとイメージの列をバインド解除されました |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
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
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c5129c6b865723721bbb6f176893c950cdf905fe
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074367"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Vs をバインドします。バインドされない Text、Image 列
  サーバー カーソルを使用するときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーはバインドされていないため、データを転送しないように最適化されて**テキスト**、 **ntext**、または**イメージ**に列を時間**SQLFetch**を実行します。 **テキスト**、 **ntext**、または**イメージ**データが実際には取得されません、サーバーからアプリケーションの問題まで[SQLGetData](../native-client-odbc-api/sqlgetdata.md)用、列です。  
  
 多くのアプリケーションを書き込むことができるようにありません**テキスト**、 **ntext**、または**イメージ**ユーザーは単にスクロール カーソルの間のデータが表示されます。 アプリケーションが呼び出すことができますし、ユーザーは、詳細情報を表示する行を選択するときに**SQLGetData**を取得する、**テキスト**、 **ntext**、または**イメージ**データ。 こうと送信、**テキスト**、 **ntext**、または**イメージ**の任意のユーザーがいないを選択し、その行のデータが非常に大きなの転送を防ぐデータの量。  
  
## <a name="see-also"></a>参照  
 [テキストとイメージの列を管理します。](managing-text-and-image-columns.md)   
 [カーソル動作](../native-client-odbc-cursors/cursor-behaviors.md)  
  
  