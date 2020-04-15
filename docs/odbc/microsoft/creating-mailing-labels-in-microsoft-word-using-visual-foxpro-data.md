---
title: ビジュアル FoxPro データを使用して Word で宛名ラベルを作成する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro data [ODBC], mailing labels
- Visual FoxPro data [ODBC], Word
- mailing labels [ODBC]
- Visual FoxPro ODBC driver [ODBC], Word
- FoxPro ODBC driver [ODBC], word
ms.assetid: c901b60c-9f84-407a-b3d1-b4d301a71370
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c3ca6c729cfa988e2560192d705bc24e9e7b4fa1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280802"
---
# <a name="creating-mailing-labels-in-microsoft-word-using-visual-foxpro-data"></a>Visual FoxPro データを使用した Microsoft Word での宛名ラベルの作成
Windows 95 または Windows 98 ドキュメントの Word でビジュアル フォックスプロ のデータを使用できます。 たとえば、Visual FoxPro テーブルに格納されている顧客情報から宛名ラベルを作成する場合があります。  
  
### <a name="to-create-mailing-labels"></a>宛名ラベルを作成するには  
  
1.  Word で、新しい空白の文書を作成します。  
  
2.  [ツール] メニューの [差し込み印刷] をクリックします。  
  
3.  差し込み印刷ヘルパーで、[作成] を選択し、[宛名ラベル] を選択します。  
  
4.  [メイン文書] で [アクティブ ウィンドウ] を選択します。  
  
5.  [データ ソース] で 、[データの取得] を選択し、[データ ソースを開く] を選択します。  
  
6.  [データ ソースを開く] ダイアログ ボックスで、[MS クエリ] を選択します。  
  
7.  [データ ソースの選択] ダイアログ ボックスで、Visual FoxPro データ ソースを選択し、[使用] をクリックします。  
  
8.  データ ソースからアクセスするデータベースにテーブルが含まれている場合は、[テーブルの追加] ダイアログ ボックスでテーブルを選択します。 クエリ デザイナの上半分に追加されたテーブルが表示されます。  
  
9. テーブルからデザイナーの下半分にフィールドをドラッグして、クエリのフィールドを選択します。  
  
10. [ファイル] メニューの [データを Word に戻す] を選択します。 Microsoft Query が閉じ、選択したデータが差し込み印刷文書で使用できるようになります。  
  
11. [メインドキュメント] で、[設定] を選択します。  
  
12. [ラベル オプション] ダイアログ ボックスで、必要なプリンタとラベル情報を選択し、[OK] をクリックします。  
  
13. [ラベルの作成] ダイアログ ボックスで、宛名ラベルに印刷するフィールドを選択し、[OK] をクリックします。  
  
14. 差し込み印刷ヘルパーの [文書とデータを差し込む] の下にある [差し込み] をクリックします。  
  
15. [結合] ダイアログ ボックスで、必要なオプションを選択し、[マージ] をクリックします。
