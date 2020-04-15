---
title: マイクロソフトアクセスへのビジュアルフォックスプロデータのインポート |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- importing data [ODBC]
- FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], Access
- Visual FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], importing
ms.assetid: a3591295-0a76-4e3c-b4fa-8bd4f1cde705
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 90ac16bbdbaf7f4dd29e14e66cf5b9dc666057f4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302453"
---
# <a name="importing-visual-foxpro-data-into-microsoft-access"></a>Visual FoxPro データの Microsoft Access へのインポート
[インポート] オプションを使用して、Visual FoxPro データベースに格納されているデータを Access データベースにインポートできます。  
  
### <a name="to-import-visual-foxpro-data-into-a-microsoft-access-database"></a>ビジュアル フォックスプロのデータを Access データベースにインポートするには  
  
1.  Access データベースを開きます。  
  
2.  [ファイル] メニューの [外部データの取り込み] を選択してから[インポート]を選択します。  
  
3.  [インポート] ダイアログ ボックスの [ファイルの種類] ボックスの一覧で[ODBC データベース] を選択します。  
  
4.  [SQL データ ソース] ダイアログ ボックスで、クエリを実行する FoxPro データに接続する Visual FoxPro データ ソースを選択し、[OK] をクリックします。  
  
5.  [オブジェクトのインポート] ダイアログ ボックスで、インポートする 1 つまたは複数のテーブルを選択し、[OK] をクリックします。 インポートしたビジュアル FoxPro テーブルの名前が、Access データベースの [テーブル] タブに表示されます。  
  
 これで、インポートされた Visual FoxPro テーブルのデータを操作するために Access を使用できるようになりました。 インポートするデータは、Visual FoxPro に格納されているデータのスナップショットです。インポートしたデータに対する変更は、Visual FoxPro データ ソースに返されません。  
  
 Visual FoxPro データ ソースのデータを変更する変更を行う場合は[、「Access からの Visual FoxPro データのクエリと更新](../../odbc/microsoft/querying-and-updating-visual-foxpro-data-from-microsoft-access.md)」を参照してください。
