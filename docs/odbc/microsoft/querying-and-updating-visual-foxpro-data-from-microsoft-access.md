---
title: Access からビジュアル FoxPro データのクエリと更新 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f11b49ed099ba29d0e7e013af99a8ad96ca6825c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292872"
---
# <a name="querying-and-updating-visual-foxpro-data-from-microsoft-access"></a>Microsoft Access からクエリを実行して Visual FoxPro データを更新する
[リンク テーブル] オプションを使用すると、Access データベースから Visual FoxPro データベースに格納されているデータをクエリしたり更新したりできます。  
  
### <a name="to-link-a-visual-foxpro-database-to-a-microsoft-access-database"></a>ビジュアル フォックスプロ データベースを Access データベースにリンクするには  
  
1.  Access データベースを開きます。  
  
2.  [テーブル] タブで、[新規] をクリックします。  
  
3.  [新しいテーブル]ダイアログ ボックスで、[リンク テーブル]を選択して[OK]をクリックします。  
  
4.  [リンク] ダイアログ ボックスの [ファイルの種類] ボックスの一覧で [ODBC データベース] を選択します。  
  
5.  [SQL データ ソース] ダイアログ ボックスで、クエリを実行する Visual FoxPro データに接続するデータ ソースを選択し、[OK] をクリックします。  
  
6.  [テーブルのリンク] ダイアログ ボックスで、クエリおよび更新するテーブルを選択し、[OK] をクリックします。 リンクされた Visual FoxPro テーブルは、Access データベースの [テーブル] タブに表示されます。  
  
 これで、リンクされた Visual FoxPro テーブルのデータをクエリおよび更新するために Access を使用できるようになりました。 リンクされたデータに加えた変更は、Visual FoxPro データ ソースに返送されます。  
  
 Visual FoxPro データ ソースのデータに影響を与える変更を行わない場合は[、「Visual FoxPro データを Access にインポートする](../../odbc/microsoft/importing-visual-foxpro-data-into-microsoft-access.md)」を参照してください。
