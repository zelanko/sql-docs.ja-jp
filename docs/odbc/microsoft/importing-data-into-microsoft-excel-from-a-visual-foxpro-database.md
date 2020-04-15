---
title: ビジュアルフォックスプロデータベースからExcelにデータをインポートする |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- importing data [ODBC]
- FoxPro ODBC driver [ODBC], Excel
- Visual FoxPro data [ODBC], Excel
- Visual FoxPro data [ODBC], importing
- Visual FoxPro ODBC driver [ODBC], Excel
ms.assetid: 3085bc4c-00a7-40e5-bffb-c3962cd3d509
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1bfd86233e5a0a406febcb30bf7a4fae595e53d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287672"
---
# <a name="importing-data-into-microsoft-excel-from-a-visual-foxpro-database"></a>Visual FoxPro データベースから Microsoft Excel へのデータのインポート
データ ソースを定義している場合は、Visual FoxPro データを Excel ワークシートにインポートできます。 ビジュアル フォックス プロ データ ソースの作成については[、「Excel からビジュアル フォックス プロ データ ソースにアクセスする](../../odbc/microsoft/accessing-a-visual-foxpro-data-source-from-microsoft-excel.md)」を参照してください。  
  
### <a name="to-import-visual-foxpro-data-into-an-microsoft-excel-worksheet"></a>ビジュアル フォックスプロのデータを Excel ワークシートにインポートするには  
  
1.  Excel スプレッドシートを開きます。  
  
2.  [データ] メニューの [外部データの取り込み] を選択します。 クエリが開きます。  
  
3.  [データ ソースの選択] ダイアログ ボックスで、Visual FoxPro データ ソースを選択し、[使用] をクリックします。  
  
4.  データ ソースからアクセスするデータベースにテーブルが含まれている場合は、[テーブルの追加] ダイアログ ボックスでテーブルを選択します。 クエリ デザイナの上半分に追加されたテーブルが表示されます。  
  
    > [!NOTE]  
    >  ドライバは所有者をサポートしていないため、このダイアログ ボックスでは所有者リストを使用できません。 ドライバはデータ ソース内の複数のデータベースをサポートしていないため、データベースの一覧は使用できません。  
  
5.  テーブルからデザイナーの下半分にフィールドをドラッグして、クエリのフィールドを選択します。  
  
6.  クエリを閉じます。 選択したデータが Excel スプレッドシートにインポートされます。
