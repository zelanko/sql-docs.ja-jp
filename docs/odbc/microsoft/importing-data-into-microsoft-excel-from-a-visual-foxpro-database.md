---
title: "Visual FoxPro データベースから Microsoft Excel にデータをインポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing data [ODBC]
- FoxPro ODBC driver [ODBC], Excel
- Visual FoxPro data [ODBC], Excel
- Visual FoxPro data [ODBC], importing
- Visual FoxPro ODBC driver [ODBC], Excel
ms.assetid: 3085bc4c-00a7-40e5-bffb-c3962cd3d509
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3cd82106bf81b5885f74adf6c1759883110ea913
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="importing-data-into-microsoft-excel-from-a-visual-foxpro-database"></a>Visual FoxPro データベースから Microsoft Excel にデータをインポートします。
データ ソースを定義している場合は、Microsoft Excel ワークシートに Visual FoxPro データをインポートできます。 Visual FoxPro データ ソースを作成する方法の詳細については、次を参照してください。 [Visual FoxPro データ ソースから Microsoft Excel へのアクセス](../../odbc/microsoft/accessing-a-visual-foxpro-data-source-from-microsoft-excel.md)です。  
  
### <a name="to-import-visual-foxpro-data-into-an-microsoft-excel-worksheet"></a>Visual FoxPro データを Excel ワークシートにインポートするには  
  
1.  Microsoft Excel スプレッドシートを開きます。  
  
2.  [データ] メニューから、外部データの取得を選択します。 Microsoft のクエリを開きます。  
  
3.  データ ソースの選択 ダイアログ ボックスで、Visual FoxPro データ ソースを選択し、使用 をクリックします。  
  
4.  データ ソースからアクセスされるデータベースには、テーブルが含まれている場合は、テーブルの追加 ダイアログ ボックスからテーブルを選択します。 Microsoft のクエリでは、クエリ デザイナーの上部に追加されたテーブルが表示されます。  
  
    > [!NOTE]  
    >  所有者のリストは、ドライバーは所有者をサポートしていないために、このダイアログ ボックスで使用できません。 ドライバーは、データ ソース内の複数のデータベースをサポートしていないために、データベースの一覧は使用できません。  
  
5.  ドラッグして、テーブルの下半分デザイナーのクエリのフィールドを選択します。  
  
6.  Microsoft のクエリを閉じます。 選択したデータは、Microsoft Excel スプレッドシートにインポートされます。

