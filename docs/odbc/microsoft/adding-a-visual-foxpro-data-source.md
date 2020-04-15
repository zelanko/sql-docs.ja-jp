---
title: ビジュアル FoxPro データ ソースを追加する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro data source [ODBC], adding
- adding data sources [ODBC], Visual FoxPro ODBC driver
ms.assetid: 1487e188-52c8-4f48-b4fe-25a650dd9e97
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1fd0c0f929ca00b7cf731dc92f07f69b6503f884
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307143"
---
# <a name="adding-a-visual-foxpro-data-source"></a>Visual FoxPro データ ソースの追加
アプリケーションから Visual FoxPro データにアクセスするには、データ ソースが必要です。 データ ソースは次のように作成できます。  
  
-   ODBC ドライバを使用するアプリケーション® Word、Excel、または Access などのアプリケーション。  
  
-   アプリケーションの外部で、Windows ® 95、Windows 98、または Windows NT ®/Windows 2000 コントロール パネルを使用します。  
  
 データ ソースがシステムに存在した後、Visual FoxPro データにアクセスするたびに同じデータ ソースを再利用できます。 アクセスするデータベースまたはテーブルが複数ある場合は、データベースまたはディレクトリごとに別のデータ ソースを作成できます。  
  
 次の手順では、コントロール パネルを使用してデータ ソースを作成します。 アプリケーションからデータ ソースを作成する方法の詳細については、「 [Office から Visual FoxPro データにアクセスする](../../odbc/microsoft/accessing-visual-foxpro-data-from-microsoft-office.md)」を参照してください。  
  
### <a name="to-add-a-visual-foxpro-data-source"></a>データ ソースを追加するには  
  
1.  Windows 2000 を実行しているコンピュータで、Windows のコントロール パネルを開き、[管理ツール] をダブルクリックします。  
  
2.  [データ ソース (ODBC)] をダブルクリックして、[ODBC データ ソース アドミニストレータ] ダイアログ ボックスを開きます。 このアイコンは、Visual FoxPro ODBC ドライバーまたは ODBC ドライバー ソフトウェアをインストールした後に使用できます。  
  
    > [!NOTE]  
    >  以前のバージョンの Windows を実行している場合は、Windows のコントロール パネルを開き、32 ビット ODBC または ODBC をダブルクリックして[ODBC データ ソース アドミニストレータ]ダイアログ ボックスを開きます。  
  
3.  [追加] をクリックします。  
  
4.  [新しいデータ ソースの作成] ダイアログ ボックスで、[Microsoft Visual FoxPro ドライバー] を選択し、[完了] をクリックします。  
  
5.  [ODBC [Visual FoxPro セットアップ](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)] ダイアログ ボックスで、データ ソースの名前と説明を入力し、データベースの種類を選択して、データベースまたはディレクトリを選択し、[OK] をクリックします。  
  
     新しいデータ ソース名が、[ODBC データ ソース アドミニストレータ] ダイアログ ボックスの [ユーザー DSN] タブの [ユーザー データ ソース] リストに表示されます。  
  
6.  [OK] をクリックして新しいデータ ソースを保存し、[ODBC データ ソース アドミニストレータ] ダイアログ ボックスを閉じます。
