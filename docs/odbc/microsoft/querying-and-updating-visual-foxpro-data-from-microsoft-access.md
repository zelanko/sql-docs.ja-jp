---
title: クエリを実行して、Microsoft Access から Visual FoxPro データの更新 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- querying Visual FoxPro data [ODBC]
- FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], Access
- Visual FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], querying and updating
- updating Visual FoxPro data [ODBC]
ms.assetid: 2d314e78-9edf-44b2-bd8b-96784236bcbe
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1097e03c414d919a606ffd21ae50ffddf51173b7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63316760"
---
# <a name="querying-and-updating-visual-foxpro-data-from-microsoft-access"></a>Microsoft Access からクエリを実行して Visual FoxPro データを更新する
クエリを実行し、リンク テーブル オプションを使用して Microsoft Access データベースから Visual FoxPro データベースに格納されたデータを更新できます。  
  
### <a name="to-link-a-visual-foxpro-database-to-a-microsoft-access-database"></a>Visual FoxPro データベースを Microsoft Access データベースにリンクするには  
  
1.  Microsoft Access データベースを開きます。  
  
2.  [テーブル] タブから、新規をクリックします。  
  
3.  新しいテーブル ダイアログ ボックスで、リンク テーブルを選択し、ok をクリックします。  
  
4.  リンク ダイアログ ボックスで、ファイルの種類の一覧で、ODBC データベースを選択します。  
  
5.  SQL データ ソース ダイアログ ボックスで、クエリを実行し、ok をクリックしたい Visual FoxPro データに接続するデータ ソースを選択します。  
  
6.  リンク テーブル ダイアログ ボックスで、クエリおよび更新 ok をクリックするテーブルを選択します。 Visual FoxPro テーブルは、Microsoft Access データベースのテーブル タブに表示されます。  
  
 クエリおよびリンク Visual FoxPro テーブル内のデータを更新する Microsoft Access を使えるようになりました。 リンクされているデータに加えた変更は、Visual FoxPro データ ソースに送信されます。  
  
 Visual FoxPro データ ソースのデータに影響を参照して Microsoft Access で行った変更したくない場合[Visual FoxPro データを Microsoft Access にインポートする](../../odbc/microsoft/importing-visual-foxpro-data-into-microsoft-access.md)します。
