---
title: クエリを実行して、Microsoft Access から Visual FoxPro データの更新 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- querying Visual FoxPro data [ODBC]
- FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], Access
- Visual FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], querying and updating
- updating Visual FoxPro data [ODBC]
ms.assetid: 2d314e78-9edf-44b2-bd8b-96784236bcbe
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6704fb70b7c8764e0299c7334aa384410c45a0a7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32904067"
---
# <a name="querying-and-updating-visual-foxpro-data-from-microsoft-access"></a>クエリを実行して、Microsoft Access から Visual FoxPro データの更新
クエリを実行し、[リンク テーブル] オプションを使用して Microsoft Access データベースから Visual FoxPro データベースに格納されたデータを更新できます。  
  
### <a name="to-link-a-visual-foxpro-database-to-a-microsoft-access-database"></a>Visual FoxPro データベースを Microsoft Access データベースにリンクするには  
  
1.  Microsoft Access データベースを開きます。  
  
2.  [テーブル] タブから [新規] をクリックします。  
  
3.  新しいテーブル ダイアログ ボックスでは、リンク テーブルを選択し、ok をクリックします。  
  
4.  [リンク] ダイアログ ボックスには、ファイルの種類の一覧で ODBC データベースを選択します。  
  
5.  SQL データ ソース ダイアログ ボックスで、クエリを実行し、ok をクリックする Visual FoxPro データに接続するデータ ソースを選択します。  
  
6.  リンク テーブル ダイアログ ボックスでは、クエリ、更新し、ok をクリックしテーブルを選択します。 Visual FoxPro テーブルは、Microsoft Access データベースの [テーブル] タブに表示されます。  
  
 クエリおよびリンク Visual FoxPro テーブルのデータを更新する Microsoft Access を使用できます。 リンクされているデータに加えた変更は、Visual FoxPro データ ソースに送信されます。  
  
 Visual FoxPro データ ソースのデータに影響を与えるを参照して Microsoft Access で変更しないようにする場合に行う[Microsoft access の Visual FoxPro データのインポート](../../odbc/microsoft/importing-visual-foxpro-data-into-microsoft-access.md)です。
