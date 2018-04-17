---
title: Visual FoxPro データ Access へのインポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- importing data [ODBC]
- FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], Access
- Visual FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], importing
ms.assetid: a3591295-0a76-4e3c-b4fa-8bd4f1cde705
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0e6b2e882ae81c4c6faaebd550569cd3d5b73e38
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="importing-visual-foxpro-data-into-microsoft-access"></a>Microsoft Access Visual FoxPro データをインポートします。
Visual FoxPro データベースにインポートのオプションを使用して Microsoft Access データベースに格納されたデータをインポートすることができます。  
  
### <a name="to-import-visual-foxpro-data-into-a-microsoft-access-database"></a>Visual FoxPro データを Microsoft Access データベースにインポートするには  
  
1.  Microsoft Access データベースを開きます。  
  
2.  [ファイル] メニューから外部データの取得をインポートしを選択します。  
  
3.  インポート ダイアログ ボックスで、ファイルの種類 ボックス内の ODBC データベースを選択します。  
  
4.  SQL データ ソース ダイアログ ボックスでは、クエリを実行し、ok をクリックする FoxPro データに接続する Visual FoxPro データ ソースを選択します。  
  
5.  オブジェクトのインポート ダイアログ ボックスで、インポートし、ok をクリックする 1 つまたは複数のテーブルを選択します。 インポートした Visual FoxPro テーブルの名前は、Microsoft Access データベースの [テーブル] タブに表示されます。  
  
 インポートした Visual FoxPro テーブル内のデータを操作するのに Microsoft Access を使用できます。 インポートするデータは、Visual FoxPro; に格納されているデータのスナップショットインポートされたデータに加えた変更は、Visual FoxPro データ ソースには送信されません。  
  
 Visual FoxPro データ ソースのデータを変更するを参照してください Microsoft Access で行った変更する場合は[クエリの実行および Microsoft Access からの Visual FoxPro データの更新](../../odbc/microsoft/querying-and-updating-visual-foxpro-data-from-microsoft-access.md)です。
